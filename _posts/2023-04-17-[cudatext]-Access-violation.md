try workaround - close panel when opening cudatext

> on_start(self, ed_self): Called once on program start. Called early, before applying config files. ed_self is None.

```
Init: cuda_find_in_filesX
TypeError: an integer is required (got type Editor)

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "C:\Users\xxx\Downloads\app note\cudatext-windows-i386-1.188.0.0\py\cuda_find_in_filesX\cd_fif4.py", line 380, in on_start
    def on_start(self, ed_self):               return bpanel.exit_cudatext()
  File "C:\Users\xxx\Downloads\app note\cudatext-windows-i386-1.188.0.0\py\cuda_find_in_filesX\bottom_panel.py", line 229, in exit_cudatext
    app.dlg_proc(self.bottom_ed, app.DLG_HIDE)
  File "C:\Users\xxx\Downloads\app note\cudatext-windows-i386-1.188.0.0\py\cudatext.py", line 1282, in dlg_proc
    res = ct.dlg_proc(id_dialog, id_action, to_str(prop), index, index2, name)
SystemError: <built-in function dlg_proc> returned a result with an error set
ERROR: Exception in CudaText for on_start: SystemError: <built-in function dlg_proc> returned a result with an error set
```

---

> on_start2(self, ed_self): Called once on program start. Called later than on_start, after configs are applied, just before the main form shows. ed_self is None.

```
Init: cuda_find_in_filesX
ERROR: Exception in CudaText for on_start2: Access violation
TypeError: an integer is required (got type Editor)

The above exception was the direct cause of the following exception:

SystemError: <built-in function dlg_proc> returned a result with an error set
ERROR: Exception in CudaText for cuda_find_in_filesX.on_start2: SystemError: <built-in function dlg_proc> returned a result with an error set
Init: cudatext
```
