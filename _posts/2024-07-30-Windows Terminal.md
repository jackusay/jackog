---
published: true
---
## Windows Terminal

update by PowerShell

  irm bonguides.com/terminal | iex
  
```
PS C:\windows\system32> irm bonguides.com/terminal | iex

Installing Microsoft Windows Terminal...
Add-AppxPackage : 部署失敗，HRESULT 為: 0x80073D02, 無法安裝套件，因為它修改的資源目前已在使用中。
錯誤 0x80073D02: 無法安裝，因為必須關閉下列應用程式: Microsoft.WindowsTerminal_1.16.10261.0_x64__8wekyb3d8bbwe。
注意: 如需其他資訊，請在事件記錄檔中尋找 [ActivityId] eb96c246-9c2f-0002-e117-ebeb2f9cda01，或使用命令列 Get-AppPackage
Log -ActivityID eb96c246-9c2f-0002-e117-ebeb2f9cda01
位於 線路:44 字元:5
+     Add-AppxPackage WindowsTerminal.msixbundle
+     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (C:\Users\peter\...inal.msixbundle:String) [Add-AppxPackage], Exception
    + FullyQualifiedErrorId : DeploymentError,Microsoft.Windows.Appx.PackageManager.Commands.AddAppxPackageCommand


Name                      Architecture Version      PublisherId
----                      ------------ -------      -----------
Microsoft.WindowsTerminal          X64 1.16.10261.0 8wekyb3d8bbwe
```

update:
```
PS C:\Users\peter\Downloads> Add-AppxPackage Microsoft.WindowsTerminal_1.20.11781.0_8wekyb3d8bbwe.msixbundle        Add-AppxPackage : 部署失敗，HRESULT 為: 0x80073D02, 無法安裝套件，因為它修改的資源目前已在使用中。
錯誤 0x80073D02: 無法安裝，因為必須關閉下列應用程式: Microsoft.WindowsTerminal_1.16.10261.0_x64__8wekyb3d8bbwe。
注意: 如需其他資訊，請在事件記錄檔中尋找 [ActivityId] eb96c246-9c2f-0000-cda0-02ec2f9cda01，或使用命令列 Get-AppPac
kageLog -ActivityID eb96c246-9c2f-0000-cda0-02ec2f9cda01
位於 線路:1 字元:1
+ Add-AppxPackage Microsoft.WindowsTerminal_1.20.11781.0_8wekyb3d8bbwe. ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (C:\Users\peter\...bbwe.msixbundle:String) [Add-AppxPackage], Exceptio
   n
    + FullyQualifiedErrorId : DeploymentError,Microsoft.Windows.Appx.PackageManager.Commands.AddAppxPackageCommand
```
  
  
