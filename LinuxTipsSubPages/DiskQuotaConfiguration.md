# Configuration

Here's how to configure disk quotas on Linux:

1. Install the necessary packages:

```bash
apt install quota quotatool

```

1. Modify the /etc/fstab file to enable quotas on the desired filesystem by adding the usrquota and/or grpquota options. For example:

```
/dev/sdb1 /mnt/data ext4 defaults,usrquota,grpquota 0 0

```

1. Remount the filesystem to apply the changes.
2. Create the quota database files and generate the disk usage table with the quotacheck command.
3. Enable quotas with the quotaon command:

```bash
quotaon -vgu /mnt/data

```

1. Assign quotas to users or groups using the edquota or quotatool command. For example, for a user:

```bash
edquota username

```

or

```bash
quotatool -u username -bq 1G -l 2G /mnt/data

```

In the editor opened by edquota, you can set soft and hard limits for blocks (disk space) and inodes (number of files).

Quotas allow you to limit disk space usage per user or group by setting soft limits (which can be temporarily exceeded) and hard limits (which can never be exceeded).