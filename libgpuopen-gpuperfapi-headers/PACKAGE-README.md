# libgpuopen-gpuperfapi-headers - AMD GPU Performance API (GPUPerfAPI) C++ headers

This is a `build2` package for the
[`gpu_performance_api`](https://github.com/GPUOpen-Tools/gpu_performance_api)
C++ library. It provides the headers of the AMD GPU Performance API
(GPUPerfAPI, or GPA), a library which provides access to GPU performance
counters. It can help analyze the performance and execution characteristics
of applications using AMD Radeon GPUs with Vulkan, DirectX 12, DirectX 11,
and OpenGL.


## Usage

To start using `libgpuopen-gpuperfapi-headers` in your project, add the following `depends`
value to your `manifest`, adjusting the version constraint as appropriate:

```
depends: libgpuopen-gpuperfapi-headers ^4.4.103
```

Then import the library in your `buildfile`:

```
import libs = libgpuopen-gpuperfapi-headers%lib{gpuopen-gpuperfapi-headers}
```


## Importable targets

This package provides the following importable targets:

```
lib{gpuopen-gpuperfapi-headers}
```

The GPUPerfAPI headers, included with the `gpu_performance_api/` prefix (for
example, `#include <gpu_performance_api/gpu_perf_api.h>`). The Vulkan header
(`gpu_perf_api_vk.h`) includes `<vulkan/vulkan.h>` from the
`libvulkan-headers` dependency.

This package is headers only. The GPUPerfAPI runtime libraries
(`GPUPerfAPIVK`, `GPUPerfAPIGL`, `GPUPerfAPIDX11`, `GPUPerfAPIDX12`, and
`GPUPerfAPICounters`) are not included, so the `Gpa*()` functions declared in
`gpu_perf_api.h` and `gpu_perf_api_counters.h` cannot be linked against.
Instead, load the runtime library and obtain its function table with
`GpaGetFuncTable()`, either directly or with the interface loader in
`gpu_perf_api_interface_loader.h`. As in upstream, the interface loader
requires the `GpaFuncTableInfo* gpa_function_table_info` variable (initialized
to `nullptr`) to be defined in exactly one translation unit and only supports
64-bit targets.


## Configuration variables

This package provides no configuration variables.
