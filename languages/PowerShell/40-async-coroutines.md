# Template: Async & Coroutines [PRO]

**Goal:** To define the Event-based async model.

---

## 1. Pwsh 5.1 / 7+ (Common Events)
```powershell
$timer = New-Object Timers.Timer
Register-ObjectEvent -InputObject $timer -EventName Elapsed -Action {
    Write-Host "Ticked"
}
```

## 2. Pwsh 7+ (Modern Async/Await Wrapper)
```powershell
# Handling .NET Tasks (7.0+)
$task = [System.Threading.Tasks.Task]::Run({ 1..100 })
$task.Wait()
```

## 3. Portable Path
```powershell
# Waiting for completion
while (-not $task.IsCompleted) { Start-Sleep -m 100 }
```

## 4. Explicit Path
```powershell
# Using Wait-Event
Wait-Event -SourceIdentifier "MyEvent" -Timeout 10
```

# The Logic Bridge
// Logic: PowerShell does not have `async/await` keywords; it uses the `Wait()` method on .NET Task objects or the event queue.
