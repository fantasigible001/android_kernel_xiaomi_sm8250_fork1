# NoMount kernel integration

This directory vendors the kernel subsystem from
[`maxsteeel/nomount`](https://github.com/maxsteeel/nomount), upstream commit
`e2513c3ac3f91cfb7fda395d88b5344bb97398cb` (2026-10-01). `LICENSE` is copied
from that upstream revision. Keep the source and license together when updating
or redistributing this integration.

The Kconfig option is deliberately disabled by default and depends on
`CONFIG_KEYS`. The Poco F4 (`munch`) configuration enables both
`CONFIG_KEYS=y` and `CONFIG_NOMOUNT=y`; the build script checks those resolved
values before compilation. NoMount is built into the kernel for that profile,
which is required for this kernel's legacy 4.19 base. Other device profiles do
not enable it unless their defconfig is changed explicitly.

The kernel subsystem is only the in-kernel half of NoMount. Its userspace
companion/metamodule must be installed separately through a compatible
KernelSU/APatch manager. NoMount changes VFS path lookup and directory
iteration; follow the upstream project's warning and test carefully before
using it on a daily-use device.
