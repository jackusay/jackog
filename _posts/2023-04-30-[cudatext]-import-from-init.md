---
published: true
---
```py
#from . import __init__ as home #error
#from . import __init__         #error
#from . import init             #error
#from __init__ import get_url   #error
#from .mdimg import *           #error
from cuda_markdown_image.mdimg import get_url
```

import part need to use absolute path!!!
  https://stackoverflow.com/a/20010963
  
ref
https://stackoverflow.com/questions/42862042/how-to-import-from-the-init-py-in-the-same-directory