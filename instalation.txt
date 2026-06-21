# Installation Guide

This guide outlines the steps required to set up the environment for Llama.cpp, focusing on Windows installations using Vcpkg and Visual Studio.

## 🛠️ Prerequisites

Ensure you have the following tools installed:

### 1. Visual Studio
Install Visual Studio (e.g., 2019 or newer) using the following command:
```bash
winget install Microsoft.VisualStudio.2019.BuildTools --override "--add Microsoft.VisualStudio.Workload.VCTools --includeRecommended"
```

### 2. CMake
Install CMake using:
```bash
winget install kitware.CMake
```

## 📦 Setting up Vcpkg (Package Manager)

Vcpkg is used here to manage external dependencies (like `zlib`, `curl`, `openssl`).

1.  **Clone Vcpkg**:
    ```bash
    git clone https://github.com/microsoft/vcpkg.git
    cd vcpkg
    ```
2.  **Bootstrap Vcpkg**:
    Run the bootstrap script. Success will be indicated by a message showing the Vcpkg version (e.g., `vcpkg version`).
    ```bash
    bootstrap-vcpkg.bat
    ```
3.  **Update PATH**:
    Add the path to your Vcpkg directory to your system's PATH environment variable.
    *(Example: Add `C:\path\to\vcpkg` to PATH)*

## 🧩 Installing Dependencies with Vcpkg

Install the necessary libraries using Vcpkg, specifying the `x64-windows` triplet:
```bash
vcpkg install zlib curl openssl --triplet x64-windows
```

## 🚀 Setting up CUDA Toolset (If Applicable)

If you plan to use GPU acceleration with CUDA, you must configure the environment to point to the installed CUDA Toolkit.

**1. CUDA Toolkit Installation**:
Ensure you have installed the CUDA Toolkit (e.g., version 12.8), which will create a path like:
`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\`

**2. Copying Build Customizations**:
The build system needs specific files from the CUDA installation. You must copy them into the following Visual Studio BuildCustomizations folders:

*   **Visual Studio BuildTools**:
    `C:\Program Files (x86)\Microsoft Visual Studio\20xx\BuildTools\MSBuild\Microsoft\VC\vXXX\BuildCustomizations`
*   **Visual Studio Community/Professional**:
    `C:\Program Files (x86)\Microsoft Visual Studio\20xx\Community\MSBuild\Microsoft\VC\vXXX\BuildCustomizations`

> **⚠️ ATTENTION!**
> In some cases, these files might *already* exist in your folders. If they are present, **you can skip this copy step.**





