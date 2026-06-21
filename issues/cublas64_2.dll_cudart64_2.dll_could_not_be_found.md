# Error: Missing CUDA DLLs (\`cublas64_2.dll\` & \`cudart64_2.dll\`)

This document details an issue encountered during application runtime where critical CUDA Dynamic Link Libraries (DLLs) were not found, and outlines the steps taken to resolve it.

## Problem Description
Upon execution, the application reported errors specifically stating that \`cublas64_2.dll\` and \`cudart64_2.dll\` could not be located. This occurred even though the prerequisite CUDA Toolkit was confirmed to be installed correctly on the system.

## ✅ Solution Overview
The issue was successfully resolved by manually copying the required DLL files from the global CUDA installation directory into the application's local execution path.

## 🛠️ Implementation Steps
Follow these steps to replicate the fix:

1.  **Identify Source Location (CUDA Binaries):**
    *   Locate the DLLs within your CUDA installation path.
    *   *Example Path:* \`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.x\bin\`
    *   *(Note: Check for versions like \`cublas64_12.dll\`, \`cudart64_12.dll\`, etc., depending on your CUDA version.)*

2.  **Identify Destination Location:**
    *   Copy the required DLLs into the directory where the main application executable resides.
    *   *Example Path:* \`C:\llama.cpp\build\bin\Release\` (The same folder containing \`llama-cli.exe\`).

## Outcome
After completing these steps, the DLL not found errors were resolved, and the application launched successfully, confirming the fix.
