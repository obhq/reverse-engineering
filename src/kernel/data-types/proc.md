# proc

`proc` represents a single process in the system, including the [kernel](../variables/proc0.md) itself. This struct mostly the same as [FreeBSD](https://github.com/freebsd/freebsd-src/blob/release/9.1.0/sys/sys/proc.h#L479) version with some PS4 specific.

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
