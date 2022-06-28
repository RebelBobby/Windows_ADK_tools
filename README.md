# Deploying Windows using Windows ADK tools
# Use of tools included in the Windows ADK, create bootable Windows PE media, 
# prepare a Windows 10 computer to be imaged, capture a reference Windows 10 image, and deploy a captured 
# Windows 10 image.

# This is the creation and testing of a Windows 10 image to be used for a future Windows 10 desktop deployment
# Use of Hyper-V to create a virtual machines. capture images and validate that the image can be deployed to 
# new computer.

# Typical terminal commands

copype amd64 E:\WinPE
MakeWinPEMedia /ISO E:\WinPE E:\WinPE\WindowsPE_amd64.iso
netsh int ipv4 set address "Ethernet" static 10.10.0.11 255.255.255.0
net use z: \\10.10.0.10\Captures /user:userName\Administrator strongPass
dism /Capture-Image /ImageFile:z:\ImgName.wim /CaptureDir:d:\ /name:"ImgName"
netsh int ipv4 set address "Ethernet" static 10.10.0.11 255.255.255.0
net use z: \\10.10.0.10\Captures /user:userName\Administrator strongPass
Dism /apply-image /imagefile:Z:\ImgName.wim /index:1 /ApplyDir:G:\
