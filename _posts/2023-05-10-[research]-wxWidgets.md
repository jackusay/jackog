---
published: true
---
wxWidgets 3.2.2.1 Released
Posted on February 13, 2023
  https://github.com/wxWidgets/wxWidgets
  
Using Binaries
  How to install binaries depends on your platform 

building your applications with CMake
  https://docs.wxwidgets.org/latest/overview_install.html

We provide pre-built binary files for the following compilers:
  Microsoft Visual C++ compiler
  MinGW-w64
  TDM-GCC
  MSYS2 MinGW
  
binary:
you should download the "Dev" and the "ReleaseDLL" files in addition to the "Headers" one above
unzip all of them into the same directory
  https://docs.wxwidgets.org/latest/plat_msw_binaries.html
  
wxWidgets and vcpkg
  https://www.wxwidgets.org/blog/2019/01/wxwidgets-and-vcpkg/
Still no conan package... 😔
  https://www.reddit.com/r/cpp/comments/vtfyvp/wxwidgets_320_released/
  
I think it just needs API modernization. That’s it. Then it would totally rock. It could be a thin “free” (template only) wrapper.

XRC, which allows you to describe a window in an XML document much like HTML. It can be edited and live reloaded.
  https://news.ycombinator.com/item?id=32010272