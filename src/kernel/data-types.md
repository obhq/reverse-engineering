# Data Types

This is a list of data types that are using in the PS4 kernel.

## proc

This struct was derived from [FreeBSD](https://github.com/freebsd/freebsd-src/blob/release/9.1.0/sys/sys/proc.h#L479).

| 9.0   | Type              | Name              | Description |
| ----- | ----------------- | ----------------- | ----------- |
| 0x010 | thread *          | p_threads_first   ||
| 0x018 | thread **         | p_threads_last    ||
| 0x020 | mtx               | p_slock           ||
| 0x040 | ucred *           | p_ucred           ||
| 0x0A0 | sigacts *         | p_sigacts         ||
| 0x0A8 | i32               | p_flag            ||
| 0x0B0 | i32               | p_pid             ||
| 0x0D8 | proc *            | p_pptr            ||
| 0x0F8 | mtx               | p_mtx             ||
| 0x118 | ksiginfo *        | p_ksi             ||
| 0x120 | sigqueue          | p_sigqueue        ||
| 0x168 | vmspace *         | p_vmspace         ||
| 0x2B8 | vnode *           | p_textvp          ||
| 0x2D4 | i32               | p_sig             ||
| 0x300 | thread *          | p_singlethread    ||
| 0x308 | i32               | p_suspcount       ||
| 0x310 | thread *          | p_xthread         ||
| 0x330 | char *            | unk3              ||
| 0x340 | rtld *            | p_dynlib          ||
| 0x384 | u32               | unk4              | 0x02 = ET_SCE_REPLAY_EXEC |
| 0x450 | i32               | p_osrel           ||
| 0x454 | char[32]          | p_comm            ||
| 0x474 | char[1024]        | basename          ||
| 0x880 | sysentvec *       | p_sysent          ||
| 0x888 | pargs *           | p_args            ||
| 0x8AC | char[?]           | p_randomized_path ||
| 0x9AC | u16               | p_xstat           ||
| 0x9B0 | knlist            | p_klist           ||
| 0x9E0 | i32               | p_numthreads      ||
| 0xA38 | u16               | p_acflag          ||
| 0xA78 | mqueue_notifier * | p_mqnotifier      ||
| 0xA80 | kdtrace_proc *    | p_dtrace          ||
| 0xA88 | cv                | p_pwait           ||
| 0xA98 | cv                | p_dbgwait         ||
| 0xAF4 | i32               | unk1              | Seems like image type? |
| 0xB10 | char[28]          | unk2              | Seems like a struct. |
| 0xB40 | u32               | sdk_version       ||

## self_auth_info

This struct contains authorization information. The PS4 rely on this struct to determine what actions can be done for each thread (they don't use *nix permissions). The PS4 obtained this struct from application image through the SAMU. Some examples of this structs can be found [here](https://www.psdevwiki.com/ps4/Auth_Info).

| 9.0  | Type   | Name  | Description |
| ---- | ------ | ----- | ----------- |
| 0x00 | u64    | paid  | [Program Authority ID](https://www.psdevwiki.com/ps4/Program_Authority_ID) |
| 0x08 | u64[4] | caps  | Bit flags indicated what permissions are allowed. |
| 0x28 | u64[4] | attrs ||
| 0x48 | u8[64] |       ||

## thread

This struct was derived from [FreeBSD](https://github.com/freebsd/freebsd-src/blob/release/9.1.0/sys/sys/proc.h#L204).

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
