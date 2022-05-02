# rsync command

## Commonly used options in rsync command

- `-v`
  - Verbose output
- `-q`
  - Suppress message output
- `-a`
  - Archive files and directory while synchronizing
- `-r`
  - Sync files and directories recursively
- `-b`
  - Take the backup during synchronization
- `-z`
  - Compress file data during the transfer

## remote sync with pem

- Give terminal full disk permission if you are using mac.

`sudo rsync -e "ssh -i key.pem" -zrvh ubuntu@34.72.111.237:/home/ubuntu .`

## Copy or sync files locally

`rsync -zvh [Source-Files-Dir] [Destination]`

## Copy or sync directory locally

`rsync -zavh [Source-Files-Dir] [Destination]`

## Copy files and directories recursively locally

`rsync -zrvh [Source-Files-Dir] [Destination]`

## Reference

- [rsync Command in Linux with Examples](https://linuxize.com/post/how-to-use-rsync-for-local-and-remote-data-transfer-and-synchronization/)
- [Fix Terminal “Operation not permitted” Error in macOS Monterey, Big Sur, Catalina, Mojave](https://osxdaily.com/2018/10/09/fix-operation-not-permitted-terminal-error-macos/)
