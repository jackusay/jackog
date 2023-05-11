---
published: true
---
example:
```cpp
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx]
"MUIVerb"="makeTx" ;caption in the context-menu
"icon"="F:\\blog\\demo-icon.ico"
"subCommands"=""

[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx\shell\txconvert]
"MUIVerb"="convert to .tx"
[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx\shell\txconvert\command]
@="cmd /k %%MAKETX%% \"%1\" --opaque-detect --constant-color-detect --monochrome-detect --fixnan box3 --oiio --attrib tiff:half 1 -v -u --unpremult --oiio --format exr"
```

first line:
```
Windows Registry Editor Version 5.00
```

location:
```
All Files	HKEY_CURRENT_USER\Software\Classes\*\shell\
By File Extension [1]	HKEY_CURRENT_USER\Software\Classes\SystemFileAssociations\{EXTENSION}\shell
Directories	HKEY_CURRENT_USER\Software\Classes\Directory\shell
Directories Background	HKEY_CURRENT_USER\Software\Classes\Directory\Background\shell
Drive	HKEY_CURRENT_USER\Software\Classes\Drive\shell
```

`HKEY_CURRENT_USER` #all user
`HKEY_LOCAL_MACHINE`  #only current user

MUIVerb #caption in the context-menu
icon
  absolute path
  escape backward slashes like \ -> \\ 
  only .ico file
@ #command
  escape " -> \"
  
```
[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx\command]
@="cmd /k \"\"D:\\resources\\maketx.exe\" \"%1\"\""
```
%1 variable (it simply retrieve the first argument passed to the command line, which is the path of the file)
  
delete registry file:
```
[-HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx\command]
@="cmd /k \"\"D:\\resources\\maketx.exe\" \"%1\" -v -u --unpremult --format exr\""
```

1. add Environment variable `MAKETX` in user level
2. use it:
```
[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx\command]
@="cmd /k \"\"%%MAKETX%%\" \"%1\"\" -v -u --unpremult --oiio --format exr"
```

main menu:
```
[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx]
"MUIVerb"="makeTx"

[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx\command]
@="cmd /k \"\"%%MAKETX%%\" \"%1\"\" -v -u --unpremult --oiio --format exr" 
```

sub-menus:
```
[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx]
"MUIVerb"="makeTx"
"subCommands"=""
[HKEY_CURRENT_USER\Software\Classes\*\shell\makeTx\shell\txconvert]
```

* Menus are sorted alphabetically by key name. A workaround for this would be to se a number prefix like 001txconvertsrgb

Auto-generating the .reg files
  https://github.com/MrLixm/Reg-file-creator
  
ref:
https://mrlixm.github.io/blog/windows-explorer-context-menu/