# BootXray
Visualizing Concurrency, Dependencies, and Delays during Linux Boot

Modern Linux boot is highly concurrent with drivers and services executing in parallel under complex dependency chains, interrupt driven wakeups, and asynchronous workloads.  On heterogeneous systems, even with the same code, boot behavior varies by CPU topology, making regressions hard to debug.
 
Existing tools provide limited insight. Kernel logs and journalctl are useful only when failures are explicitly reported and the initcall_debug timelines show where time is spent, but doesn’t explain why.  Tools like systemd-analyze, bootchart identifies slow components but mask systemic issues like CPU starvation, lock contention, and missed parallelism. While ftrace offers low-level visibility, correlating threads/kworkers activity to respective driver’s context is tough.
 
Drawing on years of hands on kernel boot debugging experience, we present BootXray—a trace driven observability framework that combines ftrace data with early boot kprobe events and post processing for correlation. When visualized in Perfetto, this produces a systemic view of boot behavior which can uncover the root causes invisible to traditional tools, enabling faster debug of boot issues.
