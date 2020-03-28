# Notes

Updated: Mar 28, 2020

Well. I came across the seL4 repo while reading a VEE'20 paper.
Haven't really looked into any of the L4 series kernels, first time.

The repo seems really small, I spent ~20min went though the repo, took a brief read of some files. This is just the kernel part of the seL4 project. Most of the userspace stuff are in other repos.

1. I like the `gdb-macros`, seems a very useful one. Especially if we are running stuff with QEMU. We can setup a bridge.
2. It supports arm, riscv, and x86. All arc-dependent part is really lean. Some basic stuff down there.
     - In terms of Verification, how seL4 prove it can safely run on top of so many machine platforms? There exist some machine quicks that need workarounds. Linux itself has some of those.
3. Function names are too long
4. why there are only `serial` and `timer` in drivers?
5. Code is simple, I suppose. I'm getting interested in how they do formal verification!

It's a microkernel, so most of the stuff runs in userspace.

Doc:
    - https://docs.sel4.systems/projects/user_libs/.
    - https://docs.sel4.systems/UserlandComponents
Code:
    - https://github.com/seL4/util_libs
    - https://github.com/seL4/seL4_libs

So what have I learned?
    - seL4 kernel is thin. The way it is written is interesting, much simpler than Linux.
    - The way they organize the repos are simply broken. They need to post more links within the repo itself.
    - There are many "internal infrastructures" within the project, e.g., the way library is written.
      It takes time to pick up such project because you generally need to understand these first.
    - How seL4 performs? They have a web:https://sel4.systems/About/Performance/.
      So around 1200 cycles to do an IPC for a Skylake CPU @3.4GHz. Still room for improvement.
      The fastest, of couse, is using cache coherence traffict, like ffwd, which can do one-way in 50 cycles.
      Skybridge used VMfunc to speedup. IPC is always the thing for microkernel :)
    - I'm getting interested in formal verification.
