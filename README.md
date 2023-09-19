# SynCord-linux
different kernels for enabling/disabling shuffling for spinlock/rwsem

## Description
The branch name indicates whether the kernel is for spinlock only or for both rwsem and spinlock, with syncord_should_reorder/default_cmp_func enabled/disabled. For example, for the kernel that has built-in shuffle_waiter for both spinlock and rwsem, disabled syncord_should_reorder/default_cmp_func, it will be on the branch rwsem_spin_disable.

## BPF functions, eefault enabling and disabling shuffling
The bpf functions are inserted in kernel/locking/qspinlock.c and kernel/locking/rwsem.c, which could be hooked by the ebpf. The all start with bpf_ prefix and the shuffle_waiter functions are in those files as well. Enabling and disabling shuffling are tuned by syncord_should_reorder/default_cmp_func above.
