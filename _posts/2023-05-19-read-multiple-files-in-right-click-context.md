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