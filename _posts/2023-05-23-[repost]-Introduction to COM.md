---
published: true
---

COM 

## Definitions

specifies that the binary modules (the DLLs and EXEs) must be compiled to match a specific structure.
specifies how COM objects must be organized in memory

Once that's done, the modules can be accessed easily from any programming language.

The structure of COM objects in memory just happens to use the same structure that is used by C++ virtual functions, so that's why a lot of COM code uses C++. 

COM is not Win32-specific. It could, in theory, be ported to Unix or any other OS.

An **interface** is simply a group of functions. 
Those functions are called methods. 
Interface names start with I, for example IShellLink.
In C++, an interface is written as an abstract base class that has only pure virtual functions.
COM uses (a pointer to the interface) to (access to the methods (function) of an interface).


A **coclass** (short for component object class) is contained in a DLL or EXE, and contains the code behind one or more interfaces.
The coclass is said to implement those interfaces.
A COM object is an instance of a coclass in memory.

A **COM server** is a binary (DLL or EXE) that contains on or more coclasses.
**Registration** is the process of creating registry entries that tell Windows where a COM server is located.

Each interface and coclass has a **GUID**.
UUIDs and GUIDs are, for all practical purposes, the same.

A class ID, or **CLSID**, is a GUID that names a coclass.
An interface ID, or **IID**, is a GUID that names an interface.

An **HRESULT** is an integral type used by COM to return error and success codes. 
It is not a "handle" to anything, despite the H prefix.

When you **create a COM object**, you tell the COM library what interface you need. If the object is created successfully, the COM library returns a pointer to the requested interface. You can then call methods through that pointer, just as if it were a pointer to a regular C++ object.

Whenever a COM method **returns a string**, that string will be in Unicode.
If you want to get the string into a more manageable state, you should convert it to a TCHAR string.
TCHAR and the _t functions (for example, _tcscpy()) are designed to let you handle Unicode and ANSI strings with the same source code.

## Creating a COM object

To create a COM object and get an interface from the object, you call the COM library API `CoCreateInstance()`.

When you call `CoCreateInstance()`, it handles looking up the CLSID in the registry, reading the location of the server, loading the server into memory, and creating an instance of the coclass you requested.

...

```cpp
HRESULT     hr;
IShellLink* pISL;

hr = CoCreateInstance ( CLSID_ShellLink,         // CLSID of coclass
                        NULL,                    // not used - aggregation
                        CLSCTX_INPROC_SERVER,    // type of server
                        IID_IShellLink,          // IID of interface
                        (void**) &pISL );        // Pointer to our interface pointer

    if ( SUCCEEDED ( hr ) )
        {
        // Call methods using pISL here.
        }
    else
        {
        // Couldn't create the COM object.  hr holds the error code.
        }
```

## coclass implement
Every COM interface is derived from IUnknown.
IUnknown has three methods:
AddRef()
Release()
QueryInterface() - Requests an interface pointer from a COM object. You use this when a coclass implements more than one interface.

## Bringing it All Together - Sample Code

source: 
https://www.codeproject.com/Articles/633/Introduction-to-COM-What-It-Is-and-How-to-Use-It

## theory

COM is not an object-oriented language but a standard.
COM specifies an object model and programming requirements that enable COM objects (also called COM components, or sometimes simply objects) to interact with other objects.
COM is referred to as a binary standard;

COM can use any lang.
The only language requirement for COM is that code is generated in a language that can create structures of pointers and, either explicitly or implicitly, call functions through pointers.

COM requires that the only way to gain access to the methods (function) of an interface is through a pointer to the interface.
only way to manipulate the data associated with an object is through an interface on the object.
  https://learn.microsoft.com/en-us/windows/win32/com/component-object-model--com--portal
