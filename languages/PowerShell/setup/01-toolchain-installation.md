# Template: Toolchain Installation [CORE]

**Goal:** To define the installation of PowerShell 5.1 (Windows Management Framework) and Pwsh 7+ (Cross-platform).

---

## 1. The Definition (Mental Model)
PowerShell comes in two distinct flavors:
- **Windows PowerShell (5.1):** Built on the .NET Framework. Pre-installed on Windows. Legacy.
- **PowerShell (7+):** Built on .NET Core. Cross-platform (Windows, Linux, macOS). Modern.

## 1. Pwsh 5.1 (Legacy)
Already pre-installed. To verify:
```powershell
$PSVersionTable.PSVersion
# Output: Major  Minor  Build  Revision
#         5      1      ...
```

## 2. Pwsh 7+ (Modern)
Install via `dotnet` tool or package manager.
```bash
# Linux (Ubuntu)
sudo apt install powershell -y
pwsh --version
# Output: PowerShell 7.4.x
```

## 3. Portable Path
To check if you are running in Pwsh 7+ or 5.1:
```powershell
if ($IsCoreCLR) { "Running on Pwsh 7+ (Core)" } else { "Running on Pwsh 5.1 (Framework)" }
# Output: (Dependent on host)
```

## 4. Explicit Path (7+ Install via Winget)
```powershell
winget install --id Microsoft.Powershell --source winget
```

# The Logic Bridge
// Logic: PowerShell 7+ runs side-by-side with 5.1; they use different executable names (`pwsh` vs `powershell`).
