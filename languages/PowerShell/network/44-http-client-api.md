# Template: HTTP Client API [PRO]

**Goal:** To define `Invoke-RestMethod` and `HttpClient`.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
# Slow, uses IE engine internally
Invoke-WebRequest -Uri "https://api.github.com"
```

## 2. Pwsh 7+ (Modern)
```powershell
# Fast, uses HttpClient natively
Invoke-RestMethod -Uri "https://api.github.com/zen"
```

## 3. Portable Path
```powershell
# Standard JSON fetch
$data = Invoke-RestMethod -Uri "https://jsonplaceholder.typicode.com/posts/1"
$data.title
```

## 4. Explicit Path (High-Performance HttpClient)
```powershell
$client = [System.Net.Http.HttpClient]::new()
$task = $client.GetStringAsync("https://google.com")
$task.Result
```

# The Logic Bridge
// Logic: PowerShell 7+'s `Invoke-RestMethod` is a wrapper around `HttpClient`, whereas 5.1 uses `WebRequest` which is significantly heavier.
