

# AFP to SMB

Switching from AFP (Apple Filing Protocol) to SMB (Server Message Block) is now recommended as AFP is deprecated and SMB is the default for modern macOS and cross-platform environments.

## Steps to Switch from AFP to SMB

- **Enable SMB on your Server/NAS**: Ensure your server or NAS has SMB enabled. This is often available in the device’s settings under “Windows File Service” or similar. [reddit](https://www.reddit.com/r/synology/comments/1mlod5r/switching_from_afp_to_smb_for_time_machine_on/)
    
- **Disable AFP**: To avoid confusion and auto-reconnection with AFP, disable the AFP service before connecting via SMB. [geraldonit](https://www.geraldonit.com/apple-afp-to-smb-migration-removing-appledouble-and-_-files-and-converting-file-names-from-unicode-nfd-to-nfc/)
    
- **Reconnect on Mac Clients**: Remove the old AFP connection in Finder or your backup software (like Time Machine), then add the share again using SMB (e.g., `smb://servername/sharename`). For Time Machine, create a new backup destination using the SMB path. [rockstor](https://forum.rockstor.com/t/migrating-time-machine-from-afp-to-samba/6871)
    
- **Copy or Migrate Data**:
    
    - On a Mac: Mount both AFP & SMB shares, then copy files directly—this will handle resource fork conversion automatically, but be aware that copying might be slow and can be interrupted by file locks. [workflowhelp.kodak](https://workflowhelp.kodak.com/display/PRINSAG100/Moving+files+from+an+AFP+tertiary+server+to+an+SMB+tertiary+server)
        
    - On Windows: Use tools like Robocopy to migrate files from AFP to SMB mounts. For complex workflows (e.g., if resource forks matter), specific utilities (such as Kodak’s ForkTranslator) may help with AppleDouble and alternate data streams conversion. [workflowhelp.kodak](https://workflowhelp.kodak.com/display/PRINSAG100/Moving+files+from+an+AFP+tertiary+server+to+an+SMB+tertiary+server)
        
    - Check your files afterward to confirm no data—especially macOS metadata or “resource forks”—is lost in migration. Some files (e.g., those with special characters, tags, or complex metadata) may not migrate perfectly. [qnap](https://forum.qnap.com/viewtopic.php?p=435005&sid=3f07c0a0f1708a7e7839c39070b3c80f)
        
- **Spotlight, Tags, and Compatibility**: Some macOS-specific features like Spotlight and Finder tags may not transfer or work identically over SMB, and some servers require enabling specific compatibility options (like “vfs_fruit” or Apple-style encoding). [truenas](https://www.truenas.com/community/threads/migrating-afp-to-smb.55003/)
    

## Things to Watch For

- **File Naming Issues**: Files with certain special characters in names (supported by AFP but not SMB) may see their names altered or become unreadable, especially on some NAS or server platforms. [qnap](https://forum.qnap.com/viewtopic.php?p=435005&sid=3f07c0a0f1708a7e7839c39070b3c80f)
    
- **AppleDouble Files**: macOS may create hidden ._ (AppleDouble) files to store resource forks on SMB shares; this is normal, but there may be extra hidden files visible on Windows.
    
- **Performance**: Copying many small files will result in twice as many files on SMB due to AppleDouble, impacting performance. Large file performance is not usually affected. [workflowhelp.kodak](https://workflowhelp.kodak.com/display/PRINSAG100/Moving+files+from+an+AFP+tertiary+server+to+an+SMB+tertiary+server)
    

## Best Practices

- Make a full backup before starting the migration.
    
- Disable AFP after switching to avoid accidental reconnects or confusion.
    
- Test SMB access thoroughly with all operating systems you support.
    
- For Time Machine, start a new backup if possible, as direct migration of existing AFP Time Machine backups to SMB is not always supported. [rockstor](https://forum.rockstor.com/t/migrating-time-machine-from-afp-to-samba/6871)
    
- If you have special workflows (like print or media workflows involving resource forks), consult specific documentation for your hardware/software, or consider using utilities designed for those migrations. [workflowhelp.kodak](https://workflowhelp.kodak.com/display/PRINSAG100/Moving+files+from+an+AFP+tertiary+server+to+an+SMB+tertiary+server)
    

In summary, the process usually involves enabling SMB, disabling AFP, reconnecting clients, and migrating data with attention to metadata and compatibility quirks. For most home and small office users, it’s straightforward, but large or specialized environments may need extra steps to preserve all data and metadata. [truenas](https://forums.truenas.com/t/migrating-afp-share-to-smb/35433)

Sources:
- https://www.macworld.com/article/234926/using-afp-to-share-a-mac-drive-its-time-to-change.html
- https://www.geraldonit.com/apple-afp-to-smb-migration-removing-appledouble-and-_-files-and-converting-file-names-from-unicode-nfd-to-nfc/
