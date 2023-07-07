# fast_syscall

This is an entry point of `syscall` instruction. It is almost identical to the [FreeBSD](https://github.com/freebsd/freebsd-src/blob/release/9.1.0/sys/amd64/amd64/exception.S#L346) version. It use standard System V AMD64 ABI for kernel interface the same as [Linux](https://stackoverflow.com/a/2538212/1829232), except `rax` is an actual `errno` in case of error (not a negative `errno` like Linux). The `rax` and `rdx` is also used for storing the return value. The `CF` on rFLAGS will be set if `rax` is an `errno`. In this case the `rax` will never be a zero.

## Locations

| Version | Offset     |
| ------- | ---------- |
| 9.0     | 0x000001C0 |
