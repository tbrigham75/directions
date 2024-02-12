Restore LXC:
 pct restore 101 vzdump-lxc-101-2023_05_15-12_12_43-docker01.tar --storage local-zfs

 Restore VM:
 qmrestore vzdump-qemu-100-2023_05_18-22_20_45-dc01.vma.zst 100 --storage local-zfs  