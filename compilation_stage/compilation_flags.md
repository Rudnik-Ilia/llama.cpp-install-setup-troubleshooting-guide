# Compilation Flags for llama.cpp

---

## GPU Backends

-DGGML_CUDA=ON  
Enables NVIDIA CUDA backend. Offloads computation to RTX GPUs.

-DGGML_VULKAN=ON  
Enables Vulkan backend for cross-platform GPU acceleration.

-DGGML_METAL=ON / OFF  
Apple Metal backend (macOS only).

-DGGML_HIPBLAS=ON  
AMD ROCm/HIP acceleration.

-DGGML_SYCL=ON  
Intel SYCL backend for Intel GPUs.

-DGGML_OPENBLAS=ON  
CPU matrix acceleration via OpenBLAS.

---

## CPU Optimizations

-DGGML_NATIVE=ON  
Enables full native CPU instruction set (AVX2/FMA/etc).

-DGGML_AVX2=ON / OFF  
Manually toggles AVX2 support.

-DGGML_AVX512=ON / OFF  
Enables AVX-512 (if supported).

-DGGML_FMA=ON / OFF  
Enables fused multiply-add instructions.

-DGGML_CPU_ALL_VARIANTS=ON  
Builds all CPU instruction variants and selects best at runtime.

---

## Build Configuration

-DCMAKE_BUILD_TYPE=Release  
Optimized production build (-O3).

-DCMAKE_BUILD_TYPE=Debug  
Debug build with symbols.

-DBUILD_SHARED_LIBS=ON  
Builds dynamic libraries.

-DGGML_BACKEND_DL=ON  
Dynamic backend loading.

-DGGML_LLAMAFILE=ON / OFF  
CPU SGEMM optimization layer.
