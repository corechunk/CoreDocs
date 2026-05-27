# Template: Linking & Delivery [SYSTEMS]

**Goal:** To define P/Invoke (Calling C APIs).

---

## 1. Pwsh 5.1 (Legacy)
```powershell
$signature = @"
[DllImport("user32.dll")]
public static extern bool MessageBox(IntPtr hWnd, String text, String caption, uint type);
"@
Add-Type -MemberDefinition $signature -Name "Win32" -Namespace "API"
```

## 2. Pwsh 7+ (Modern Linux)
```powershell
# Calling libc on Linux
$sig = '[DllImport("libc")] public static extern int getpid();'
Add-Type -MemberDefinition $sig -Name "Libc" -Namespace "POSIX"
```

# The Logic Bridge
// Logic: `Add-Type` compiles C# code in the background using the CSC or Roslyn compiler to create a bridge to unmanaged DLLs.
