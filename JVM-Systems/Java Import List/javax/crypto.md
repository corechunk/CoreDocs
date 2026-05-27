# Package: javax.crypto
## Cryptography Operations

Classes and interfaces for cryptographic operations (Encryption, Key Generation).

### Key Classes

| Class | Purpose |
| :--- | :--- |
| **Cipher** | Provides the functionality of a cryptographic cipher for encryption/decryption. |
| **KeyGenerator** | Used to generate secret keys for symmetric algorithms. |
| **SecretKey** | Represents a secret (symmetric) key. |
| **Mac** | Message Authentication Code functionality (Hashing with a key). |

### Key Methods in Cipher

| Method | Returns | Description |
| :--- | :--- | :--- |
| `getInstance(transform)` | `Cipher` | (Static) Returns a Cipher object for the specified algorithm. |
| `init(mode, key)` | `void` | Initializes the cipher with a key and a mode (ENCRYPT_MODE/DECRYPT_MODE). |
| `doFinal(byte[])` | `byte[]` | Finishes a multiple-part encryption or decryption operation. |
| `update(byte[])` | `byte[]` | Continues a multiple-part encryption or decryption operation. |
