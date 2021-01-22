# fstab-Memento

fstab (**F**ile **S**ystem **tab**le) is a file configuration that let us to define how and where disk partitions should be mounted into the filesystem. It contains a table representation of each file system, where they are mounted, what type of filesystem used, type of mounting, ...

Each filesystem is described in a separate line.  
Each line is composed of 6 columns separated by a blank space or a tabulation.

Here are the columns :  
`<filesystem>   <mounting path>   <filesystem type>  <options>   <dump>  <fsck>`

Example of a fstab content :  
`UUID=swswswsw-r2d2-cp30-&bb8-swswswswswsw  /  ext4  defaults  0 1`

## filesystem column

The first column indicates the filesystem (partition, disk, ...). It can be specified with different options

- Descriptors `/dev/sda1`
- Labels `LABEL=HOME`
- UUIDs `UUID=abcdef...`
- GPT parition UUIDs `PARTUUID=`
- GTP patition labels `PARTLABEL=HOME`


## Mounting path column

## Type column

## Options column

## Dump column

## Fsck column

