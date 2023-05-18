---
published: true
---
## A New Post

install
https://github.com/ge9/ExecuteCommand-Pipe

```reg
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\SOFTWARE\Classes\*\shell]

[HKEY_CURRENT_USER\SOFTWARE\Classes\*\shell\makeTx]
"MUIVerb"="makeTx"

[HKEY_CURRENT_USER\SOFTWARE\Classes\*\shell\makeTx\command]
"DelegateExecute"="{FFA07888-75BD-471A-B325-59274E734000}"
```

```reg
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\SOFTWARE\Classes\CLSID\{FFA07888-75BD-471A-B325-59274E73400A}]
"AppId"="{FFA07888-75BD-471A-B325-59274E73400A}"
@="ExecuteCommand Verb Sample"

[HKEY_CURRENT_USER\SOFTWARE\Classes\CLSID\{FFA07888-75BD-471A-B325-59274E73400A}\LocalServer32]
@="C:\\Users\\peter\\Downloads\\build\\ExecuteCommand400A.exe"
```

result:
![23-05-18-14-08-54-explorer_xJSX9UDF5k.jpg]({{site.baseurl}}/img/23-05-18-14-08-54-explorer_xJSX9UDF5k.jpg)
