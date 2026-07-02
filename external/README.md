# LibreHardwareMonitor native dependencies

Place LHM-CppExport `.dll` and `.lib` files in the architecture-specific folder
that matches the Visual Studio platform being built:

```text
external\x64\*.dll
external\x64\*.lib
external\ARM64\*.dll
external\ARM64\*.lib
```

The `Release-LHM|x64` and `Debug-LHM|x64` configurations link against
`external\x64` and copy only DLLs from that folder into the output directory.

The upstream LHM-CppExport solution currently defines x86/x64 configurations,
but not an ARM64 configuration. `Release|ARM64` is available without LHM
support. `Release-LHM|ARM64` is present so it can consume native ARM64
LHM-CppExport binaries when they are available; it fails early with a clear
message if `external\ARM64` has not been populated.
