# ClamAV on Windows

## Installation

Open Powershell and install scoop
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

Install ClamAV
```
scoop install vim clamav 

vim C:\Users\<username>\scoop\apps\clamav\current\freshclam.conf

```

Comment the "example" line

```
# Comment or remove the line below.
Example
```

## Update the database

```
freshclam
```

## Scanning

Scan the whole disk

```
sudo clamscan --recursive C:\
```

Scan a specific folder

```
clamscan C:\Users\toto\Downloads
```

Scan a specific file
```
clamscan contacts.txt
```