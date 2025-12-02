
### **How to do Custom Drive Icons in windows**

* **Step 1**: Open Powershell as Adminstrator
* **Step 2**: Add the registry paths:
`New-Item -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\DriveIcons\D" -Force`

`New-Item -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\DriveIcons\D\DefaultIcon" -Force` replace D with the correct drive letter.

* **Step 3**: Set the icon
`Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\DriveIcons\D\DefaultIcon" -Name "(default)" -Value "C:\Icons\FileName.ico"
`

* **Step 4**:  Reload explorer.