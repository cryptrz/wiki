# ClamAV on MacOS

## Installation

```
brew install clamav

mv /usr/local/etc/clamav/freshclam.conf.sample /usr/local/etc/clamav/freshclam.conf

vim /usr/local/etc/clamav/freshclam.conf

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
sudo clamscan --recursive /
```

Scan a specific folder

```
clamscan /Users/toto/Downloads
```

Scan a specific file
```
clamscan contacts.txt
```