# fstab-Memento

fstab (**F**ile **S**ystem **tab**le) is a file configuration that let us to define how and where disk partitions should be mounted into the filesystem. It contains a table representation of each file system, where they are mounted, what type of filesystem used, type of mounting, ...

Each filesystem is described in a separate line.  
Each line is composed of 6 columns separated by a blank space or a tabulation.

Here are the columns :  
`<filesystem>   <mounting path>   <filesystem type>  <options>   <dump>  <fsck>`

Example of a fstab content :  
`UUID=swswswsw-r2d2-cp30-&bb8-swswswswswsw  /home  ext4  defaults  0 1`

## filesystem column

The first column indicates the filesystem (partition, disk, ...). It can be specified with different options

- Descriptors `/dev/sda1`
- Labels `LABEL=HOME`
- UUIDs `UUID=abcdef...`
- GPT parition UUIDs `PARTUUID=`
- GTP patition labels `PARTLABEL=HOME`

## Mounting path column

The second column indicates the mounting point in the OS filesystem. It can be any folder in the filesystem.
> For a partition that doesn't have a mounting point (like swap parition), we can use the value `none`.

## Type column

The third column indicates the type of filesystem used for the partition.

For instance : ext2, ext3, ext4, xfs, btrfs, vfat, swap, ...

> For ntfs we have to install ntfs-3g

## Options column

The fourth column indicates some particluar options for during the mounting process. They are the same options used with the command `mount` :

| option   | description                                                                                                    |
| -------- | -------------------------------------------------------------------------------------------------------------- |
| defaults | default options if we don't really know the others options :) eauivalent to rw,suid,dev,exec,auto,nouser,async |
| auto     | the filesystem should be automatically mounted at start up or when the command `mount -a` is executed          |
| noauto   | only mounted when we told it to be mounted                                                                     |
| exec     | binaries can be executed                                                                                       |
| noexec   | binaries can't be executed                                                                                     |
| user     | users can mount the filesystem (without root privileges)                                                       |
| nouser   | only root can mount the filesystem                                                                             |
| ro       | mount as read-only                                                                                             |
| rw       | mount as read and write                                                                                        |
| sync     | I/O done synchronously (handle single process)                                                                 |
| async    | I/O done asynchronously (can handle mutltiple I/O)                                                             |
| suid     | authorize suid and sgid (get the owner permissions when executing the owner's binary)                          |
| nosuid   | unauthorize suid and sgid                                                                                      |
| discard  | activate TRIM option on SSD (better data management)                                                           |
| nofail   | allow the boot sequence to continue even if the drive fails to mount                                           |
| ...      | ...                                                                                                            |

> These options can be mixed together with a `,`.
> Example : `UUID=swswswsw-r2d2-cp30-&bb8-swswswswswsw  /home   ext4    async,auto,noexec   0 1`

## Dump column

The fifth column indicates the dump option. Dump is a backup programm. If the value is set to 1, the filesystem will be backup with dump and not if it's set to 0.
> The programm dump nis needed for this option, it is usually not installed so it can be set to 0.

## Fsck column

The sixth column indicates the fsck (**F**ile **S**ystem **C**heck). It will check the integrity of the filesystem by priority :  

- Value 1, it will be checked first.
- Value 2, it will be checked after 1.
- Value 0, it won't be checked.

___
Updated : 23/01/2021  
Author : AnthonyF
