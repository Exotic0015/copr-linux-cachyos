<div align="center">
 
  <h1 align="center">linux-cachyos-bore for Fedora</h1>
</div>

# KERNEL

### linux-cachyos-bore-eevdf uses as default the EEVDF-BORE scheduler
- **(BORE) - Burst-Oriented Response Enhancer) CPU Scheduler** by [firelzrd (BORE)](https://github.com/firelzrd/bore-scheduler/tree/main/eevdf-bore-dev)
- **(EEVDF) - Earliest Eligiable Virtual Deadline First** [EEVDF](https://lwn.net/Articles/927530/) is a replacement for the CFS Scheduler from Peter Zijlstra

### linux-cachyos-bore uses as default the BORE scheduler
- **(BORE) - Burst-Oriented Response Enhancer) CPU Scheduler** by [firelzrd (BORE)](https://github.com/firelzrd/bore-scheduler/tree/main/bore-stable)

### Features:
- AMD PSTATE Guided Driver enabled by default and with enhancements patches/fixes.
- Latest BTRFS and XFS improvements & fixes.
- Latest & improved ZSTD 1.5.5 patch-set.
- UserKSM daemon from pf.
- Improved BFQ Scheduler.
- Back-ported patches from `linux-next`.
- BBRv3 tcp_congestion_control.
- Scheduler patches from linux-next/tip.
- General improved sysctl settings and upstream scheduler fixes.
- OpenRGB and ACS Override support.
- HDR Patches for AMD GPU's and gamescope.
- Default support for Steam Deck.
- Lenovo Legion [Patchset](https://github.com/johnfanv2/LenovoLegionLinux)
- Surface [Patches](https://github.com/linux-surface/linux-surface)
- Latest kvm-lru patches from upstream

### Checking for the cpu support:
Check support by the following the command
```
/lib64/ld-linux-x86-64.so.2 --help | grep "(supported, searched)"

```
If it does not detect x86_64_v3 support do not install the kernel. Otherwise you will end up with a non-functioning operating system! 

### Installation instructions:

#### Fedora Workstation

```
sudo dnf copr enable bieszczaders/kernel-cachyos
```

and next

```
sudo dnf install kernel-cachyos-bore
```

OR
```
sudo dnf install kernel-cachyos-bore-eevdf
```

#### Fedora Silverblue

```
cd /etc/yum.repos.d/

sudo wget https://copr.fedorainfracloud.org/coprs/bieszczaders/kernel-cachyos/repo/fedora-$(rpm -E %fedora)/bieszczaders-kernel-cachyos-fedora-$(rpm -E %fedora).repo
```

and next

```
sudo rpm-ostree override remove kernel kernel-core kernel-modules kernel-modules-core kernel-modules-extra --install kernel-cachyos-bore

sudo systemctl reboot
```

OR
```
sudo rpm-ostree override remove kernel kernel-core kernel-modules kernel-modules-core kernel-modules-extra --install kernel-cachyos-bore-eevdf

sudo systemctl reboot
```

# UKSMD

Check description [here](https://github.com/CachyOS/uksmd).

### Installation instructions:

#### Fedora Workstation

```
sudo dnf copr enable bieszczaders/kernel-cachyos-addons
```

### Install required packages:

```
sudo dnf install libcap-ng libcap-ng-devel procps-ng procps-ng-devel
```

### Install UKSMD:

```
sudo dnf install uksmd
```

### Enable UKSMD:

```
sudo systemd enable uksmd && sudo systemd start uksmd
```

### Checking the correct operation of the uksmd:

```
systemctl status uksmd
```

and

```
uksmdstats
```

#### Fedora Silverblue

```
cd /etc/yum.repos.d/

sudo wget https://copr.fedorainfracloud.org/coprs/bieszczaders/kernel-cachyos-addons/repo/fedora-$(rpm -E %fedora)/bieszczaders-kernel-cachyos-addons-fedora-$(rpm -E %fedora).repo
```

### Install required packages:

```
sudo rpm-ostree install libcap-ng-devel procps-ng-devel
```

### Install UKSMD:

```
sudo rpm-ostree install uksmd

sudo systemctl reboot
```

### Enable UKSMD:

```
sudo systemd enable uksmd && sudo systemd start uksmd
```

### Checking the correct operation of the uksmd:

```
systemctl status uksmd
```

and

```
uksmdstats
```
