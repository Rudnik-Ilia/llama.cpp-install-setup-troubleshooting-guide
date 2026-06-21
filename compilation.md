### Compilation Guide (Windows & CUDA Optimized)

Follow these steps to compile Llama.cpp, especially when using Visual Studio and Vcpkg for a CUDA build.

**1. Create Directory Structure**

Navigate to your `llama.cpp` folder and create a build directory:
```bash
# Command executed in the llama.cpp directory
mkdir build
cd build
```

**2. CMake Configuration & Generation**

Run CMake from within the `build` directory to configure the project. This example uses Visual Studio 2019, targets x64, enables CUDA, and integrates with Vcpkg.

```bash
cmake .. -G "Visual Studio 16 2019" -A x64 -DLLAMA_CUDA=ON -DGGML_VULKAN=OFF -DLLAMA_CURL=ON -DLLAMA_OPENSSL=ON -DCMAKE_TOOLCHAIN_FILE=C:/vcpkg/scripts/buildsystems/vcpkg.cmake -DCMAKE_GENERATOR_TOOLSET="cuda=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vXX.X"
```
*   **Note**: Replace `vXX.X` with your installed CUDA version (e.g., `v12.8`).
*   **Note**: Additional flags ans meannings:
[Open CMake command](../compilation_stage/compilation_flags.md)

**3. Build the Project**

Build the project using CMake:
```bash
cmake --build . --config Release
```
*   **Patience**: Be prepared! This process can take more than 40 minutes depending on your hardware.
You can decrease the time by adding:
```
--parallel 8
``` 
8 - number of cores.

*   **Warnings**: Don't worry too much about "yellow warnings"—they are usually informational and fine.

**4. Verification**

After successful compilation, you should find several executable files in:
`llama.cpp\build\bin\Release\`
These include:
*   `llama-server.exe`
*   `llama-cli.exe`

**5. Recompilation (If Necessary)**

If you need to recompile the project, it is recommended to first remove the existing `build` folder:
```bash
# Use this command in the llama.cpp directory
rmdir /q /s build
```
