---
published: false
---

How to merge two command class?

cd_fif4.py:
```py
class Command:
```

bottom_panel.py:
```py
class Command:
```

`__init__.py`:
```py
from .bottom_panel import *
from .cd_fif4 import *
```

result:
```py
AttributeError: 'Command' object has no attribute 'show_dlg'
ERROR: Exception in CudaText for cuda_find_in_filesX.show_dlg: AttributeError: 'Command' object has no attribute 'show_dlg'
```

---

cd_fif4.py:
```py
class Command:
```

bottom_panel.py:
```py
from .cd_fif4 import *
#from .cd_fif4 import Command
class Command_B(Command):

    def __init__(self):
        super().__init__()
```

`__init__.py`:
```py
from .bottom_panel import *
```
or

```py
from .cd_fif4 import *
from .bottom_panel import *
```
or

```py
from .bottom_panel import *
from .cd_fif4 import *
```

result:
```
Traceback (most recent call last):
  File "C:\Users\xxx\Downloads\app note\cudatext-windows-i386-1.188.0.0\py\cuda_find_in_filesX\__init__.py", line 1, in <module>
    from .bottom_panel import *
  File "C:\Users\xxx\Downloads\app note\cudatext-windows-i386-1.188.0.0\py\cuda_find_in_filesX\bottom_panel.py", line 34, in <module>
    class Command_B(Command):
NameError: name 'Command' is not defined
ERROR: Exception in CudaText for cuda_find_in_filesX.close_console: NameError: name 'Command' is not defined
```

ref https://stackoverflow.com/questions/15720593/python-two-modules-and-classes-with-the-same-name-under-different-packages
https://stackoverflow.com/questions/42859849/python-importing-two-modules-that-have-the-same-class-name

cudatext.
