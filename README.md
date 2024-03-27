# Building libhv with Bazel

This repository demonstrates how to build and use the [libhv](https://github.com/ithewei/libhv) network library with the [Bazel](https://bazel.build/) build system.

## Prerequisites

- Linux operating system
- Bazel 4.0.0 or later
- GCC compiler

## Building the Example

To build the `http_server` example, run:

```bash
bazel build http_server
```

The resulting binary will be located at `bazel-bin/http_server`.

Alternatively, you can run the example directly with:

```bash
bazel run http_server
```

## Using libhv in Your Bazel Project

To use libhv in your own Bazel project:

1. Add the following to your `WORKSPACE` file:

```python
git_repository(
    name = "libhv",
    remote = "https://github.com/Edward-Elric233/libhv.git",
    branch = "feature/bazel",
)
```

2. In your `BUILD` file, add `@libhv` to the `deps` attribute of your `cc_binary` or `cc_library` rule:

```python
cc_binary(
    name = "your_target",
    srcs = ["your_source.cpp"],
    deps = ["@libhv//:libhv"],
)
```

Now you can `#include` headers from libhv in your source files.

## Contributing

If you encounter any issues or have suggestions for improvements, please feel free to open an issue or submit a pull request.
