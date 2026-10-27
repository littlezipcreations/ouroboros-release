This, as you might have guessed, is a README of the Ouroboros operating system.
I will first explain how this kernel is run on my system (or if you are savvy-enough, on any system). Then will follow a breakdown of the kernel, and then design paradigms and aspirations.

## How to run Ouroboros (my way)
Ouroboros is designed for Arm Cortex CPUs, with the Arm Cortex-A76 the focus (although it runs on any such CPU at least as early as the Arm Cortex-A53 being the earliest I have tested). I do not plan to support x86-64 CPUs, RISC V CPUs or any other aarch64 CPUs.
I personally use QEMU to run Ouroboros, with my script found in [`build-and-run.sh`](build-and-run.sh)
This is a bash script designed to run on raspbian, with my setup. If you aren't compiling the kernel, and just want to run it, you only need:
> qemu-system-aarch64 -M virt -global virtio-mmio.force-legacy=false -cpu cortex-a76 -m 512M -kernel ouroboros -drive if=none,file=ouroboros.img,format=raw,id=ouroDisk -device virtio-blk-device,drive=ouroDisk -device virtio-gpu-device -nographic

(This is presuming you are looking at the release repo, and not the source.)
Graphics for Ouroboros is not finished in this version, but it inits correctly, and so I will leave it in the kernel.
For this to work, you need a version of QEMU that can run aarch64 CPUs on your computer. This can be found:
>https://www.qemu.org/download/

but I will leave this to you to work out.

Please remember to unpack the image, there are no tools on this repo to create the image with shell included, and the kernel is useless without the shell.

