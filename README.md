# process_handle [![Build Status](https://travis-ci.org/JustasMasiulis/process_handle.svg?branch=master)](https://travis-ci.org/JustasMasiulis/process_handle) [![Build status](https://ci.appveyor.com/api/projects/status/3osunqdm82hkg3is?svg=true)](https://ci.appveyor.com/project/JustasMasiulis/process-handle)
A cross platform wrapper around system native handles that allows copying and RAII based leak freedom.

## installation
the library is headers only so copying it into your project directory and including it is enough.

## quick reference
Default constructed process_handle is a handle to our own process.
It is also possible to construct process_handle using a process id
or an already existing handle.
It is safe to inherit from process_handle because it has protected destructor.
```c++
#include "process_handle.hpp"

jm::process_handle h;
h.owner_id(); // will be our own process id
auto native_handle = h.native(); // returns the OS specific native handle
if(h) { // conversion operator to bool
	h.reset(); // invalidates the handle stored in h
	h.reset(native_handle); // or replaces it with a new one
}
```
