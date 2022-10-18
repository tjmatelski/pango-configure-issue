# pango-configure-issue
Issue when using pkg-config to configure pango library installed with vcpkg

## Replicating Issue

- `git clone --recurse-submodules https://github.com/tjmatelski/pango-configure-issue.git`

- `cd pango-configure-issue; ./extern/vcpkg/bootstrap-vcpkg.sh`

- `cmake -S . -B ./build -DCMAKE_TOOLCHAIN_FILE=./extern/vcpkg/scripts/buildsystems/vcpkg.cmake`

## Error

```
CMake Error in CMakeLists.txt:
  Imported target "PkgConfig::PANGO_LIB" includes non-existent path

    "<path to where you cloned>/pango-configure-issue/extern/vcpkg/packages/pango_x64-linux/lib/pkgconfig/../../include/harfbuzz"

  in its INTERFACE_INCLUDE_DIRECTORIES.  Possible reasons include:

  * The path was deleted, renamed, or moved to another location.

  * An install or uninstall procedure did not complete successfully.

  * The installation package was faulty and references files it does not
  provide.
```