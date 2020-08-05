# LLVM Bazel BUILD files

DISCLAIMER: This is not an officially-supported Google project and is still in
development.

This repo contains standalone Bazel BUILD configuration for part  of the
[LLVM project](http://llvm.org/) that could be shared by dependent projects
using the Bazel build system.

It is branched off of the BUILD files for
[LLVM](https://github.com/tensorflow/tensorflow/blob/master/third_party/llvm/llvm.autogenerated.BUILD)
and [MLIR](https://github.com/tensorflow/tensorflow/blob/master/third_party/mlir/BUILD)
in the [TensorFlow](http://tensorflow.org) project, but aims to be
suitable for more general usage.

# Status

`bazel build --config=generic_clang @llvm-project//mlir/...` builds. Cuda and
Vulkan support are disabled.

`bazel build --config=generic_clang @llvm-project//...` has many issues with
finding `.inc` files. These issues also exist in the BUILD files used by TF.


# Generating BUILD files

Build files can be generated from LLVMBuild.txt files by running the provided
script.

```shell
sed -i '/Begin autogenerated content/Q' llvm-bazel/llvm/BUILD \
    && llvm-bazel/generate_bazel_build.py \
    --llvm_root=third_party/llvm-project/llvm \
    >> llvm-bazel/llvm/BUILD

```

# License
Licensed under the Apache license with LLVM Exceptions. See [LICENSE](LICENSE)
for more information.
