---
title: "SCVMM Gen2 VM Change Boot Order"
created: 2021-02-22
date: 2021-02-22
categories: 
  - vdi
tags: 
  - citrix
  - pxe
  - scvmm
  - virtual-machine
  - vm
authors: 
  - thecd
description: "How to change boot order for a Gen2 VM in SCVMM. Allowing you to network boot a Gen2 VM for PXE booting."
---

Recently, I found myself needing to change the boot order of a VM in System Center Virtual Machine Manager. However, I couldn't find an option to alter the boot order within the GUI properties of SCVMM.

It seems that the preferred method for changing the boot order for SCVMM's is to use PowerShell.

For my use case, I needed to make the NIC the first boot device, as it turns out it's pretty simple to do this. By doing the following, I made my NIC default, allowing me to PXE boot to SCCM for task sequencing.

Open up a PowerShell terminal

First, we need to set a variable for the exact VM we want to modify.

```
$VM = GetSCVirtualMachine -Name "name of your vm with the quotes"
```

Next, we tell SCVMM to change the first boot device for this VM.

```
Set-SCVirtualMachine -VM $VM -FirstBootDevice "NIC,0"
```

That's it, now the VM will boot to the network device first until it's changed again. If you need to boot to the hard disk first, you could use SCSI,0,0 instead of NIC,0. Also note, you may need to change the numbers to match your specific VM.
