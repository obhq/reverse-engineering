# thread

`thread` represents a single thread in a process. This struct mostly the same as [FreeBSD](https://github.com/freebsd/freebsd-src/blob/release/9.1.0/sys/sys/proc.h#L204) version with some PS4 specific.

| 9.0   | Type        | Name          | Description |
| ----- | ----------- | ------------- | ----------- |
| 0x008 | proc *      | td_proc       | The process of this thread. |
| 0x088 | i32         | td_tid        | Thread ID. |
| 0x090 | sigqueue    | td_sigqueue   | Pending signals. |
| 0x0D4 | i32         | td_flags      ||
| 0x0D8 | i32         | td_inhibitors ||
| 0x0DC | i32         | td_pflags     ||
| 0x0E8 | void *      | td_wchan      ||
| 0x130 | ucred *     | td_ucred      ||
| 0x220 | u32         | td_pticks     ||
| 0x270 | i32         | td_xsig       ||
| 0x284 | char[32]    | td_name       ||
| 0x2A8 | file *      | td_fpop       ||
| 0x2B0 | i32         | td_dbgflags   ||
| 0x388 | pcb *       | td_pcb        ||
| 0x390 | i32         | td_state      ||
| 0x398 | i64[2]      | td_retval     | `rax` and `rdx` to return from current syscall. |
| 0x3A8 | callout     | td_slpcallout ||
| 0x3E0 | trapframe * | td_frame      | User space CPU states. |
| 0x438 | i32         | td_errno      ||
