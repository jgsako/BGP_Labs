# Importing VM Images
</br>

### VSphere </br>
Importing the Ubuntu 20.04 Image into Ubuntu is actually quite easy. Right-click on a folder in the right-hand sidebar of the vSphere GUI. Click **Deploy OVF Template** -> Select **Local File** for the OVF Import -> Select all 4 files within **VSphere** Folder 

</br>

### ESXI </br>
It is preferred to download [[Notepad++](https://notepad-plus-plus.org/downloads/v8.3.3/)] so that a .OVF file can be edited easier. </br>
</br>
Installing on ESXI is very similar to the vSphere installation. There is only one difference, and that is a modification of the .OVF file. ESXI has multiple versions of VMX support, find the version that you are running on change the value of *VMX-19* to a supported VMX value by the ESXI version that you are using. (i.e. ESXI 6.7 supports only VMX-8, VMX-9, VMX-10, VMX-11, VMX-12, VMX-13, VMX-14, VMX-15)
</br></br>

### Proxmox </br>
Proxmox is far different than the other two previously mentioned installations. First the .qcow2 file needs to be added to the local storage of Proxmox (/var/lib/vz/). WinSCP or FTP, or other methods, can be used to transfer the .qcow2 file to Proxmox's internal storage. Afterward the file is copied, create an empty VM and *Detach* the Hard Disk and *Remove* the Hard Disk. Afterwards run the command: </br> 
`qm importdisk NameOfImportingVM.qcow2` </br>
</br>
This will import the .qcow2 to the local-lvm storage. After it is in local-lvm you can *Add Device* of a Hard Disk to the empty VM that was created earlier and select the imported disk storage from the previous step for the Hard Disk. When botting the VM enter "ESC" to get to the boot menu and boot from the storage file.
