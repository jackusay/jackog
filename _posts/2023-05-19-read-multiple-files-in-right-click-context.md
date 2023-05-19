---
published: true
---
## useless

### MultiSelectModel

```reg
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Classes\*\shell\Cloud]
@="XXA"
"MultiSelectModel"="Player"

[HKEY_CURRENT_USER\Software\Classes\*\shell\Cloud\command]
@="cmd /k \"\"C:\\Users\\eight\\Downloads\\a1\\b.bat\" \"%1\"\""

;C:\Users\eight\Downloads\a1
```

```bat
@echo off
echo %1 
echo %2 
echo %3
echo %*
```

result:
every instance recieve one parameter.

ref
https://superuser.com/questions/1196100/custom-windows-context-menu-shell-command-targetting-documents-docx-and-pdf

## useful

### context-menu-launcher

depends on 3rd exe

```reg
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Classes\*\shell\Cloud]
@="XXA"
"MultiSelectModel"="Player"

[HKEY_CURRENT_USER\Software\Classes\*\shell\Cloud\command]
@="\"C:\\Users\\eight\\Downloads\\a1\\singleinstance.exe\" \"%1\" \"C:\\Users\\eight\\Downloads\\a1\\b.bat\" $files --si-timeout 400"

;C:\Users\eight\Downloads\a1
```

```bat
@echo off
echo %1 
echo %2 
echo %3
echo %*

pause
```

ref
https://github.com/zenden2k/context-menu-launcher

### https://github.com/ge9/ExecuteCommand-Pipe

Register as a class
Simply double-click to run ExecuteCommandXXXX.exe

```reg
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\SOFTWARE\Classes\*\shell\makeTx]
"MUIVerb"="AmakeTx"

[HKEY_CURRENT_USER\SOFTWARE\Classes\*\shell\makeTx\command]
"DelegateExecute"="{FFA07888-75BD-471A-B325-59274E73400A}"
```

```reg
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\SOFTWARE\Classes\CLSID\{FFA07888-75BD-471A-B325-59274E73400A}]
"AppId"="{FFA07888-75BD-471A-B325-59274E73400A}"
@="ExecuteCommand Verb Sample"

[HKEY_CURRENT_USER\SOFTWARE\Classes\CLSID\{FFA07888-75BD-471A-B325-59274E73400A}\LocalServer32]
@="\"C:\\Users\\peter\\Downloads\\build\\ExecuteCommand400A.exe\" p \"C:\\Program Files\\Git\\bin\\bash.exe\" -c \"cat > $HOME/out.txt\" "
```

* After the modification, rename "LocalServer32" to any other name and then return it back.

it works.

---
no sure how to input parameter

```reg
@="\"C:\\Users\\peter\\Downloads\\build\\ExecuteCommand400A.exe\" p \"C:\\Users\\peter\\a4\\b.bat\" "
```

this no work.
