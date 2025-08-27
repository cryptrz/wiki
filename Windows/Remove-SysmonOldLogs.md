# Remove old logs created by Syslog

1. Open your favorite **text editor** and **create the file** `Remove-SysmonOldLogs.ps1`

2. **Copy / paste this code** into it (Adapter the `$Folder` variable if needed)

```powershell
$Folder = "C:\Sysmon"
$Days = 30
Get-ChildItem -Path $Folder -Recurse -File | Where-Object {
    ($_.LastWriteTime -lt (Get-Date).AddDays(-$Days))
} | Remove-Item -Force
```
3. **Save it** and **execute manually** or using the **Task Scheduler**
