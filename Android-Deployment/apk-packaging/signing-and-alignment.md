# 🔒 APK Alignment & Cryptographic Signing

Before an APK can be installed on an Android device, it must undergo **ZIP Alignment** to optimize performance, and be **Cryptographically Signed** to pass system security verifications.

---

### 1. ZIP Alignment: The Physics of 4-Byte Alignment

Android's dynamic linker accesses assets inside the APK directly using memory mapping (`mmap`). For this to work efficiently without copying data to heap memory, uncompressed resources (like images and native `.so` files) must be aligned to **4-byte boundaries** relative to the start of the file.

```text
Unaligned APK (Slow, requires memory copying):
[ Header ][ Unaligned Resource: Offset 103 ] -- mmap fails! Copies to RAM.

Aligned APK (Fast, zero-copy pointer access):
[ Header ][ Padding ][ Aligned Resource: Offset 104 ] -- mmap matches CPU word size!
```

We use the NDK `zipalign` tool to achieve this:
`zipalign -v -f 4 app-unsigned.apk app-aligned.apk`

---

### 2. Cryptographic Signing: The Chain of Trust

Android checks signatures before installing or updating apps. Modern Android uses the **v2/v3 Signing Schemes**, which embed signatures directly into the ZIP Central Directory block rather than the files themselves.

```bash
# Step 1: Create a release keystore containing your private key (run once)
keytool -genkey -v -keystore release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias release_key

# Step 2: Sign your aligned APK using apksigner
apksigner sign --ks release-key.jks --out app-signed.apk app-aligned.apk

# Step 3: Verify the signatures are valid
apksigner verify --verbose app-signed.apk
```
