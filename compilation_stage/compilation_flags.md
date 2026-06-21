# Compilation Flags for Llama.cpp

---

-DGGML_CUDA=ON - Enables NVIDIA CUDA backend. Uses CUDA kernels (nvcc) to offload transformer layers, attention, and matrix multiplication to NVIDIA GPUs.
-DGGML_VULKAN=ON - Enables Vulkan compute backend. Cross-platform GPU acceleration for AMD/Intel/NVIDIA GPUs. Usually slower than CUDA on NVIDIA hardware.
-DGGML_METAL=ON / OFF - Enables or disables Apple Metal backend (macOS only). ON is default on Apple Silicon systems.
-DGGML_HIPBLAS=ON - Enables AMD ROCm/HIP backend. Used for AMD Radeon GPUs with HIPBLAS acceleration.
-DGGML_SYCL=ON - Enables Intel SYCL backend. Targets Intel Arc and Intel data-center GPUs (Flex/Max series). Experimental compared to CUDA.
-DGGML_OPENBLAS=ON - Enables OpenBLAS CPU acceleration library. Improves matrix multiplication performance in CPU-only or fallback scenarios.

CPU Instruction Set Optimizations

-DGGML_NATIVE=ON - Builds optimized binary for the current CPU (-march=native). Enables all available SIMD instructions (AVX2, FMA, AVX512 if supported). Not portable to other CPUs.
-DGGML_AVX2=ON / OFF - Manually enables or disables AVX2 SIMD instructions. Mostly redundant when GGML_NATIVE is enabled.
-DGGML_AVX512=ON / OFF - Enables AVX-512 SIMD instructions on supported CPUs. Often unavailable or disabled on consumer Intel laptops.
-DGGML_FMA=ON / OFF - Enables Fused Multiply-Add instructions for faster floating-point matrix computation. Usually auto-detected.
-DGGML_CPU_ALL_VARIANTS=ON - Builds multiple optimized instruction-set versions (SSE, AVX, AVX2, AVX512) and selects best at runtime dynamically.

Build & System Configuration

-DCMAKE_BUILD_TYPE=Release - Enables maximum compiler optimization (-O3 equivalent), disables debug symbols, and produces production-performance binaries.
-DCMAKE_BUILD_TYPE=Debug - Enables debugging symbols and disables heavy optimizations. Used for development only.
-DBUILD_SHARED_LIBS=ON - Builds llama.cpp as shared libraries (.dll/.so/.dylib) instead of static binary. Useful for embedding in other software.
-DGGML_BACKEND_DL=ON - Enables dynamic loading of GPU backends at runtime (CUDA/Vulkan/CPU). Allows one binary to adapt to different hardware.
-DGGML_LLAMAFILE=ON / OFF - Enables or disables llamafile SGEMM CPU optimization layer. Improves small-context CPU prompt processing performance when enabled.

According to ChatGPT:

-DGGML_CUDA=ON - Enables RTX 4050 GPU acceleration (main performance gain)
-DGGML_NATIVE=ON - Enables AVX2 + FMA automatically for Intel 12th Gen CPU
-DGGML_FMA=ON - Extra SIMD floating-point boost (safe redundancy, but stable gain)
-DGGML_OPENBLAS=ON - Improves CPU fallback math performance when GPU is saturated
-DCMAKE_BUILD_TYPE=Release - Maximum compiler optimization (-O3 equivalent)
-DBUILD_SHARED_LIBS=OFF - Faster static binary execution (less overhead on Windows)
-DGGML_BACKEND_DL=ON - Allows flexible backend loading (CUDA/CPU hybrid safety)
-DGGML_LLAMAFILE=ON - Faster prompt ingestion and CPU-side optimizations

OPTIONAL (only if you want max experimentation)

Add this if you want experimental max throughput (not always stable):

-DGGML_CUDA_FORCE_MMQ=ON
