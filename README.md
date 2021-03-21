# Prebuilt V8 Binaries 💼

V8 is an open source JavaScript and WebAssembly engine created by Google which is used globally in Google Chrome, Node.Js, Deno, and many other technologies. The V8 engine can be embedded into any C++ project by linking the required libraries and importing the necessary header files. As a result of V8's huge feature set and complete implementation of the ECMAScript standard, it has a notoriously large code base. Building V8 from source can be cumbersome and time consuming, so to aid in project which must embed the engine we've created this repository which will automatically compile and release (or produce artifacts) of monolithic static V8 libaries.

**✔️ Supported platforms:** Windows x86 64-bit, and Linux x86 64-bit
<br>
**⚠️ Unsupported platforms:** MacOS x86 64-bit ( Current builds for MacOS produce problematic builds which generate massive static libraries )
<br>

**Targeted V8 Version:** The version of V8 which is being compiled can be found in the `V8_VERSION` file.
<br>

**Project Layout:** Google's GN build system utilizes `args.gn` files to define the parameters for a build, to access the build arguments for a specific platform you can navigate to the `platforms/` directory, and then the respective subdirectory for your targeted platform.

### Customize Build Arguments

If you need to change the build arguments for your specific application, you can easily fork this repository, edit the proper `args.gn` file and then push your changes. The GH Actions workflow will automatically detect and re-run the build process.

### Commit Prefixes

The workflow responsible for building the V8 libraries recognises a couple prefixes to control the behavior of the build.

| Prefix | Behavior |
| ------ | -------- |
| [Skip] | The workflow will **not** run if this prefix is present. |
| [Release] | The workflow wil release the compiled binaries and acquired header files. |

**ℹ️ Notes:**
- Only use the `[Skip]` prefix when updating documentation or non-build-impacting files. Any changes to build configurations or V8 versions must be rebuilt to assure the master branch is always working.

- Only use the `[Release]` prefix on a known-good V8 version and ensure the V8 version being released hasn't been previously released. This ensures the produced binaries are stable and prevents an influx of meaningless releases.
