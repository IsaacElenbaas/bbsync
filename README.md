# bbsync
## About
bbsync is a multithreaded bidirectional file synchronization script written in bash with minimal dependencies. It uses http(s) for transfers to straightforwardly be available behind most firewalls.

Symlinks are followed when updating their contents, but are created as normal files/folders if they do not exist on the other end.

[Demo](https://drive.google.com/file/d/1DZsCTDCf0aTLRmstR76YPTwkOL3mBR_e/preview)

I use it to sync files between various machines while maintaining one master copy. Inspired in part by [bsync.](https://github.com/dooblem/bsync)
## Dependencies
* GNU Coreutils
* `bash` 4 or above
* `find`
* `curl`

## Usage
```
./bbsync [OPTIONS]
  --connect-timeout NUM     maximum time in seconds to allow connection attempts
  -d, --dry-run             perform a trial run with no changes made
  --force [push, pull]      ignore master/local state
  --max-time NUM            maximum time in seconds to allow transfers
  --minshow NUM             minimum time in seconds to show actions
  --no-progress             do not show progress during transfer
  -p, --processes NUM       number of processes to use
  --server URL              master server URL
  -v, --verbose             output a diagnostic for every file that will be processed
  -h, --help                display this help
```
## Downsides
* No moved files detection
* File ownership is ignored, although missing write permissions is handled
* It is assumed that files will be changed only on one end before a sync due to the 'master server' philosophy
* A http(s) server implementation is required, and I (at least at the moment) am not releasing mine
