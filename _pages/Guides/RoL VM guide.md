---
title: "Setting up Roblox on Linux via KVM/QEMU"
tags:
    - guide
    - gaming
    - linux
date: "2024-07-03"
thumbnail: "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.xboxone-hq.com%2Fimages%2Fgames%2Fscreenshots%2F541-roblox-screenshot-1-1627550705.jpg&f=1&nofb=1&ipt=ed06dea38ff63dba4ddebd3840ef8e22279b9313769a1ff741d27db152d3400e&ipo=images"
bookmark: true
---

A big thank you to keyemail, who originally crafted this guide within VinegarHQ's Discord server and has assisted numerous people over there. They're awesome!

# Intro
***
This guide details the process of running Roblox within a VM using KVM/QEMU through Libvirt. While the longevity of this setup remains uncertain, we're confident it won't be dead by tomorrow.

This guide is intended for users on Debian/Ubuntu, Arch, or any of their derivatives, so long as they are using systemd.

If this guide appears overly complex, you may consider exploring an [alternative guide](https://ios7.xyz/rol-with-waydroid-guide-2/) that explains how to set up Roblox in an Android emulator using Waydroid.

# Prerequisites
***
* A secondary GPU is required for GPU passthrough. For configuring single GPU passthrough, utilize [this guide](https://github.com/ilayna/Single-GPU-passthrough-amd-nvidia/) in conjunction with ours.
* Hyper-V is essential in this guide as it enables you to play with the anti-tamper system in effect.
* A foundational understanding of Linux

### BIOS Configuration


1. Ensure that Vt-d (Intel) or AMD-Vi (AMD) is enabled in the BIOS menu.
1. Verify if Virtualization is enabled in your BIOS settings.

### Enabling IOMMU groups for Intel
(AMD Users dont have to worry about this if its enabled on the BIOS)

Add `intel_iommu=on` to the kernel parameters and ensure that `iommu=pt` is included as well (in Grub, systemdboot, etc.). Following this, reboot.

# Installing QEMU/KVM with Libvirt
***

### Arch


```
$ pacman -S qemu libvirt edk2-ovmf virt-manager ebtables dnsmasq
$ systemctl enable --now libvirtd.service
$ systemctl enable --now virtlogd.socket
$ virsh net-autostart default
$ virsh net-start default
```

Launch the Virtual Machine Manager and check if it boots successfully. It should start up; if not, there has been an issue.

### Debian/Ubuntu

This guide assumes that you have sudo configured for both your system and your current user.

````
$ sudo apt update; sudo apt upgrade -y
$ sudo apt install qemu qemu-kvm qemu-systems qemu-utils libvirt-clients libvirt-daemon-system virtisnt virt-manager -y
````

Launch the Virtual Machine Manager and check if it boots successfully. It should start up; if not, there has been an issue.

# Setting up secondary GPU passthrough with OVMF
***

### Verifying IOMMU groups

To confirm its enabled, use `$ dmesg | grep -i -e DMAR -e IOMMU`. The output should resemble the following.

```
[    0.000000] ACPI: DMAR 0x00000000BDCB1CB0 0000B8 (v01 INTEL  BDW      00000001 INTL 00000001)
[    0.000000] Intel-IOMMU: enabled
[    0.028879] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.028883] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.028950] IOAPIC id 8 under DRHD base  0xfed91000 IOMMU 1
[    0.536212] DMAR: No ATSR found
[    0.536229] IOMMU 0 0xfed90000: using Queued invalidation
[    0.536230] IOMMU 1 0xfed91000: using Queued invalidation
[    0.536231] IOMMU: Setting RMRR:
[    0.536241] IOMMU: Setting identity map for device 0000:00:02.0 [0xbf000000 - 0xcf1fffff]
[    0.537490] IOMMU: Setting identity map for device 0000:00:14.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537512] IOMMU: Setting identity map for device 0000:00:1a.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537530] IOMMU: Setting identity map for device 0000:00:1d.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537543] IOMMU: Prepare 0-16MiB unity mapping for LPC
[    0.537549] IOMMU: Setting identity map for device 0000:00:1f.0 [0x0 - 0xffffff]
[    2.182790] [drm] DMAR active, disabling use of stolen memory
```

If you see `[    0.000000] Intel-IOMMU: enabled`, you are all set!

Next, you will need to confirm that your GPU is allocated to its dedicated IOMMU Group. If it is not, you may need to perform additional patching, which is beyond the scope of this guide. Execute the following script:

```
shopt -s nullglob
for g in $(find /sys/kernel/iommu_groups/* -maxdepth 0 -type d | sort -V); do
    echo "IOMMU Group ${g##*/}:"
    for d in $g/devices/*; do
        echo -e "\t$(lspci -nns ${d##*/})"
    done;
done;
```

And the output should resemble the following:

```
IOMMU Group 1:
    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
IOMMU Group 2:
    00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:0e31] (rev 04)
IOMMU Group 4:
    00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:0e2d] (rev 04)
IOMMU Group 10:
    00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:0e26] (rev 04)
IOMMU Group 13:
    06:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] [10de:13c2] (rev a1)
    06:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller [10de:0fbb] (rev a1)
    ```

Observe how group 13 exclusively contains the graphics cards! It is acceptable to have a PCIe Express line in the group, but nothing else should be present. Additionally, remember to record the IDs enclosed in brackets (e.g., [10de:0fbb] and [10de:13c2]). Both of these IDs will be required later on, so ensure to save them!

Next, modify your mkinitcpio and confirm that these are in `MODULES`:

`MODULES=(... vfio_pci vfio vfio_iommu_type1 ...)`

If you have an Nvidia card, ensure that these are placed in FRONT to prevent potential errors.

Finally, we need to isolate the card, so execute the following command:
`$ nano /etc/modprobe.d/vfio.conf`

And insert the ID tags you saved earlier using this command:
`options vfio-pci ids=10de:13c2,10de:0fbb`

Now, execute `$ mkinitcpio -P` to apply it across all your kernels and then reboot.

# Setting up Virtual Machine Manager.
***
Execute Virtual Machine Manager, and customize it to your preferences. **However,** before finalizing the setup, ensure to select "Customize Installation before Install." In the Overall tab, confirm that your chipset is Q35 and your firmware is UEFI (with Secure Boot for Windows 11). Proceed with the installation process as usual.

After completing the installation, boot up the VM and access the configuration area once more. Be prepared to edit some XML files, so ensure that XML editing is enabled by navigating to Edit -> Preferences -> Enable XML Editing.

For some Nvidia users, ensure to add BOTH PCIe devices (Nvidia Card and Nvidia Audio) by including the first PCIe numbers along with the card name in brackets.

Next, remove the spice graphics by setting the `Video` module to `None`. Delete the sound card (right-click), eliminate the USB redirects, and ensure that the `<audio>` tag at the bottom of the XML file specifies:

```
<audio id="1" type="none"/>
```

You should be able to remove `Display Spice`, followed by `Video`.

Here is where the section on "Getting the anticheat to work with the VM" comes into play. We will configure Hyper-V (Nested Virtualization) to deceive the anti-tamper tool, rendering it unaware that we are operating within a virtual machine.

In your XML file, within the `<features>` section all the way down to `</features>`, insert the following:

```
<features>
    <acpi/>
    <apic/>
    <pae/>
    <hap state="on"/>
    <privnet/>
    <hyperv mode="passthrough">
      <relaxed state="on"/>
      <vapic state="on"/>
      <spinlocks state="on" retries="8191"/>
      <vpindex state="on"/>
      <runtime state="on"/>
      <synic state="on"/>
      <stimer state="on"/>
      <reset state="off"/>
      <vendor_id state="on" value="PS3000X"/>
      <frequencies state="on"/>
      <reenlightenment state="off"/>
      <tlbflush state="on"/>
      <ipi state="on"/>
      <evmcs state="off"/>
    </hyperv>
    <kvm>
      <hidden state="on"/>
      <hint-dedicated state="on"/>
      <poll-control state="on"/>
      <pv-ipi state="on"/>
    </kvm>
    <vmport state="off"/>
    <smm state="on"/>
    <ioapic driver="kvm"/>
  </features>
  ```

  This is one part of the step; next, navigate to your `<cpu>` tag, which should be located directly below `<features>`, and ensure that these two lines are included.

```
  <feature policy="require" name="hypervisor"/>
<feature policy="require" name="vmx"/>
```

For example, it should appear as follows:

```
<cpu mode="custom" match="exact" check="partial">
    <topology sockets="1" dies="1" cores="5" threads="1"/>
    <feature policy="require" name="hypervisor"/>
    <feature policy="require" name="vmx"/>
</cpu>
```

If for any reason, your VM is stuck in a boot loop, consider adding this:

```
<model fallback="allow">Skylake-Client-noTSX-IBRS</model>
```

Example:

```
<cpu mode="custom" match="exact" check="partial">
    <model fallback="allow">Skylake-Client-noTSX-IBRS</model>
    <topology sockets="1" dies="1" cores="5" threads="1"/>
    <feature policy="require" name="hypervisor"/>
    <feature policy="require" name="vmx"/>
</cpu>
```

# Conclusion
***
If you have followed all the steps correctly, you should now be within a Windows VM, ready to download and enjoy playing Roblox!

Depending on your preferences, you can utilize a playbook to optimize Windows, providing a significant performance enhancement. However, this does strip UAC and Windows Defender, so proceed with caution if that is of concern to you.

For a simpler approach, you can try [Azurite Optimizer,](https://tweakcentral.net/downloads) which can enhance the speed of your Windows installation slightly.

Alternatively, consider using [winutil,](https://github.com/ChrisTitusTech/winutil) an Open Source tool that offers numerous privacy, security, and debloating options, ultimately improving performance as well.
