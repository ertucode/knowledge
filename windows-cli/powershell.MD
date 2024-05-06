# Show folder sizes descending

```powershell
ls -Force | Add-Member -Force -Passthru -Type ScriptProperty -Name Length -Value {ls $this -Recurse -Force | Measure -Sum Length | Select -Expand Sum } | Sort-Object Length -Descending | Format-Table @{label="TotalSize (MB)";expression={[Math]::Truncate($_.Length / 1MB)};width=14}, @{label="Mode";expression={$_.Mode};width=8}, Name
```

# Kill process at port

```powershell
netstat -ano | findstr "PID :PortNumber"
taskkill /PID pidNumber /F
Get-Process -Id $PID
```
