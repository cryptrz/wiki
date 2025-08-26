# ClamAV on Debian-based distributions

## Installation

```
sudo apt install install clamav clamav-daemon

```

(Optional) Graphical interface
```
sudo apt install clamtk

```

## Update the database

```
sudo freshclam
```

## Scanning

Scan the whole disk

```
sudo clamscan --r /
```

Scan a specific folder

```
clamscan -r /Users/toto/Downloads
```

Scan a specific file

```
clamscan contacts.txt
```
