| Hive Name       | Contains                                                                                     | Location                                                                 |
|-----------------|----------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|
| SYSTEM          | Services, Mounted Devices, Boot Configuration, Drivers, Hardware                            | `C:\Windows\System32\config\SYSTEM`                                     |
| SECURITY        | Local Security Policies, Audit Policy Settings                                               | `C:\Windows\System32\config\SECURITY`                                   |
| SOFTWARE        | Installed Programs, OS Version, Autostarts, Program Settings                                 | `C:\Windows\System32\config\SOFTWARE`                                   |
| SAM             | Usernames and their Metadata, Password Hashes, Group Memberships, Account Statuses          | `C:\Windows\System32\config\SAM`                                        |
| NTUSER.DAT      | Recent Files, User Preferences, User-specific Autostarts                                     | `C:\Users\<username>\NTUSER.DAT`                                         |
| USRCLASS.DAT    | Shellbags, Jump Lists                                                                        | `C:\Users\<username>\AppData\Local\Microsoft\Windows\USRCLASS.DAT`      |

---

| Hive on Disk    | Where You See It in Registry Editor                                          |
|-----------------|----------------------------------------------------------------------------------------------|
| SYSTEM          | `HKEY_LOCAL_MACHINE\SYSTEM`                                                   |
| SECURITY        | `HKEY_LOCAL_MACHINE\SECURITY`                                                 |
| SOFTWARE        | `HKEY_LOCAL_MACHINE\SOFTWARE`                                                 |
| SAM             | `HKEY_LOCAL_MACHINE\SAM`                                                      |
| NTUSER.DAT      | `HKEY_USERS\<SID>` and `HKEY_CURRENT_USER`                                    |
| USRCLASS.DAT    | `HKEY_USERS\<SID>\Software\Classes`                                           |

---

| Registry Key                                                                                   | Role                                                                                          |
|------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USBSTOR`                                     | Stores information about USB devices connected to the system (make, model, device ID).       |
| `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU`                | Stores commands typed by the user in the Run dialog (`Win + R`).                              |
| `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist`            | Stores information on recently accessed applications launched via the GUI.                   |
| `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPaths`            | Stores paths and locations typed by the user in the Explorer address bar.                    |
| `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\App Paths`                      | Stores the paths of installed applications.                                                   |
| `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\WordWheelQuery`        | Stores search terms typed by the user in the Explorer search bar.                            |
| `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run`                           | Stores programs set to automatically start when the user logs in (startup programs).         |
| `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs`            | Stores information on recently accessed files.                                                |
| `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName`               | Stores the computer's name (hostname).                                                       |
| `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall`                      | Stores information on installed programs.                                                     |
