---
description: Run in the browser with WebAssembly
---

# Running in the Browser

It is currently very early days and not ready for production, however if you want to test this exciting new feature please take the following steps.

1. Install ```wasm-tools``` workload tools. See [dotnet documentation](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-workload-install).

2. Install or update the dotnet templates to the latest version (0.10.11 or above).

```bash
dotnet new -i avalonia.templates
```

3. Create a new directory for the project.

```bash
mkdir WebTest
cd WebTest
```

4. Generate a new project that supports running in the browser.

```bash
dotnet new avalonia.xplat
```

5. In order to run simply do:

```bash
cd WebTest.Web
dotnet run
```

## Troubleshooting
If you have not performed the step to install `wasm-tools`, you will encounter errors when running the app in your browser later (e.g. `System.DllNotFoundException: libSkiaSharp`) and you will need to rebuild again before the app will run.
