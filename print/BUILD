load("@mypy_integration//:mypy.bzl", "mypy_test")
load("@rules_python//python:defs.bzl", "py_binary")

py_binary(
    name = "print",
    srcs = glob(["*.py"]),
    )

mypy_test(
    name = "print_mypy",
    deps = [
        ":print",
        ]
    )

