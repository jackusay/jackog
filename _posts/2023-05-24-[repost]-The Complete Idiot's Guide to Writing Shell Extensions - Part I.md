---
published: true
---
The Complete Idiot's Guide to Writing Shell Extensions - Part I
  https://www.codeproject.com/Articles/441/The-Complete-Idiot-s-Guide-to-Writing-Shell-Extens

## dev

make an extension that just pops up a message box to show that it's working. We'll hook the extension up to .TXT files

### use VC, run the AppWizard and make a new ATL COM program.
### add `The Initialization Interface`
* add `IShellExtInit` in `COM_MAP`

The COM_MAP is how ATL implements QueryInterface(). It tells ATL what interfaces other programs can retrieve from our COM objects.
If we return `S_OK`, then Explorer will call QueryInterface() again and get a pointer to another interface: `IContextMenu`.

### add `The Interface for Interacting with the Context Menu`
* add `IContextMenu` in `COM_MAP`

IContextMenu has three methods:
```cpp
  STDMETHODIMP GetCommandString(UINT, UINT, UINT*, LPSTR, UINT); // Carrying out the user's selection
  STDMETHODIMP InvokeCommand(LPCMINVOKECOMMANDINFO); // show info in status bar; the status bar will show fly-by help
  STDMETHODIMP QueryContextMenu(HMENU, UINT, UINT, UINT, UINT); // add context menu
```
### register

## debug

When you cause a shell extension to be loaded by Explorer, it will stay in memory for a while, making it impossible to rebuild the DLL.

To have Explorer unload extensions more often, create this registry key:

```
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Explorer\AlwaysUnloadDLL
```

and set the default value to "1". On 9x, that's the best you can do. On NT, go to this key:

```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer
```

and create a DWORD called DesktopProcess with a value of 1.

This makes the desktop and Taskbar run in one process, and subsequent Explorer windows each run in its own process. This means that you can do your debugging with a single Explorer window, and when you close it, your DLL is automatically unloaded, avoiding any problems with the file being in use. You will need to log off and back on for these changes to take effect.

others: check `Debugging the shell extension`

## Registering the Shell Extension

```
HKEY_CLASSES_ROOT\txtfile\ShellEx\ContextMenuHandlers\SimpleShlExt
```

This has a couple of side effects

* ...
* https://stackoverflow.com/questions/2123762/add-menu-item-to-windows-context-menu-only-for-specific-filetype/47745854#47745854
* https://stackoverflow.com/questions/46930511/add-entry-to-right-click-menu-for-a-specific-filetype
