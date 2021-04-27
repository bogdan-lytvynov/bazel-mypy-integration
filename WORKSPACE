load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

####################################### Python Rules ###############################################

rules_python_version = "0.2.0"

http_archive(
    name = "rules_python",
    sha256 = "778197e26c5fbeb07ac2a2c5ae405b30f6cb7ad1f5510ea6fdac03bded96cc6f",
    urls = [
        "http://github-cache.canva-build.com/bazelbuild/rules_python/releases/download/{version}/rules_python-{version}.tar.gz".format(version = rules_python_version),
        "http://github-cache.canva-build.com/bazelbuild/rules_python/releases/download/{version}/rules_python-{version}.tar.gz".format(version = rules_python_version),
        "https://github.com/bazelbuild/rules_python/releases/download/{version}/rules_python-{version}.tar.gz".format(version = rules_python_version),
        ],
    )

load("@rules_python//python:pip.bzl", "pip_install")

pip_install(
    name = "test",
    requirements = "//test:requirements.txt",
    )

####################################### MYPY SUPPORT ###############################################
mypy_integration_version = "0.1.0" # latest @ November 15th 2020

http_archive(
    name = "mypy_integration",
    sha256 = "511ca642294129b7abebf6afd48aa63e7d91de3ec5fa0689d60d1dc6a94a7d1a",
    strip_prefix = "bazel-mypy-integration-{version}".format(version = mypy_integration_version),
    url = "https://github.com/thundergolfer/bazel-mypy-integration/archive/{version}.tar.gz".format(
        version = mypy_integration_version,
    ),
)

load(
    "@mypy_integration//repositories:repositories.bzl",
    mypy_integration_repositories = "repositories",
)
mypy_integration_repositories()

load("@mypy_integration//:config.bzl", "mypy_configuration")
# Optionally pass a MyPy config file, otherwise pass no argument.
mypy_configuration("//tools/typing:mypy.ini")

load("@mypy_integration//repositories:deps.bzl", mypy_integration_deps = "deps")

mypy_integration_deps(
    mypy_requirements_file="//tools/typing:mypy_version.txt",
)
