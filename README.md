# AzureLua

## About the project

AzureLua is a modified version of Lua 5.5.0 that uses the CMake build system primarily for embedding in Azure Games products, such as Cobalt Engine.

## Using AzureLua

To vendor AzureLua in a CMake project:
- Vendor the library and include it with `add_subdirectory(azurelua_path)`
- Link it with `target_link_libraries(target_name azurelua)`

## Credits

- Original Lua developers - Making Lua
- Azure Games - Modifying Lua to make AzureLua