# Template: Character Sets (Charset) [SYSTEMS]

**Goal:** To define how PowerShell handles strings and encoding, specifically the shift from UTF-16 (v5.1) to UTF-8 (v7+).

---

## 1. The Definition (Mental Model)
- **Pwsh 5.1:** Defaulted to **UTF-16** internally and **ANSI** for many commands. This caused issues with cross-platform files.
- **Pwsh 7+:** Defaulted to **UTF-8 (without BOM)** for everything. This is the modern global standard.

## 1. Pwsh 5.1 (Legacy)
```powershell
# Saving a file in 5.1 often defaults to UTF-16
"Hello" | Out-File -FilePath .\test.txt -Encoding unicode
```

## 2. Pwsh 7+ (Modern)
```powershell
# Saving in 7+ defaults to UTF-8
"Hello" | Out-File -FilePath .\test.txt
```

## 3. Portable Path
Always explicitly define the encoding to avoid version surprises.
```powershell
"Portable Text" | Out-File -FilePath .\out.txt -Encoding utf8
```

## 4. Explicit Path (.NET Native)
```powershell
[System.IO.File]::WriteAllText("C:\path\to\file.txt", "Explicit Text", [System.Text.Encoding]::UTF8)
```

# The Logic Bridge
// Logic: PowerShell 7+ eliminated the "Encoding" headache by standardizing on UTF-8 to align with Linux/Cloud standards.
