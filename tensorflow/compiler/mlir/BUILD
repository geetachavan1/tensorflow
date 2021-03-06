# Description:
#   TensorFlow/TensorFlow Lite/XLA MLIR dialects and tools.

load("//tensorflow:tensorflow.bzl", "tf_cc_binary")

package(
    default_visibility = ["@local_config_mlir//:friends"],
    licenses = ["notice"],  # Apache 2.0
)

package_group(
    name = "subpackages",
    packages = ["//tensorflow/compiler/mlir/..."],
)

# To reference all tablegen files here when checking for updates to them.
filegroup(
    name = "td_files",
    srcs = glob(["**/*.td"]),
)

cc_library(
    name = "tf_mlir_opt_main",
    srcs = ["tf_mlir_opt_main.cc"],
    deps = [
        "//tensorflow/compiler/mlir/lite:tensorflow_lite",
        "//tensorflow/compiler/mlir/lite:tensorflow_lite_dialect_registration",
        "//tensorflow/compiler/mlir/lite:tensorflow_lite_legalize_tf",
        "//tensorflow/compiler/mlir/lite:tensorflow_lite_optimize",
        "//tensorflow/compiler/mlir/lite:tensorflow_lite_quantize",
        "//tensorflow/compiler/mlir/tensorflow",
        "//tensorflow/compiler/mlir/tensorflow:tensorflow_dialect_registration",
        "//tensorflow/compiler/mlir/tensorflow:tf_dialect_passes",
        "//tensorflow/compiler/mlir/xla",
        "//tensorflow/compiler/mlir/xla:xla_dialect_registration",
        "//tensorflow/compiler/mlir/xla:xla_legalize_control_flow",
        "//tensorflow/compiler/mlir/xla:xla_legalize_tf",
        "//tensorflow/compiler/mlir/xla:xla_legalize_to_standard",
        "//tensorflow/core:lib",
        "@llvm//:support",
        "@local_config_mlir//:AffineDialectRegistration",
        "@local_config_mlir//:MlirOptLib",
        "@local_config_mlir//:Pass",
        "@local_config_mlir//:QuantOps",
        "@local_config_mlir//:QuantOpsDialectRegistration",
        "@local_config_mlir//:Support",
        "@local_config_mlir//test:TestDialect",
        "@local_config_mlir//test:TestTransforms",
    ],
)

tf_cc_binary(
    name = "tf-opt",
    deps = [
        ":tf_mlir_opt_main",
        "//tensorflow/compiler/mlir/tensorflow:tf_graph_optimization_pass",
    ],
)

tf_cc_binary(
    name = "tf-mlir-translate",
    deps = [
        "//tensorflow/compiler/mlir/tensorflow:convert_graphdef",
        "//tensorflow/compiler/mlir/tensorflow:mlir_roundtrip_flags",
        "//tensorflow/compiler/mlir/tensorflow:translate_cl_options",
        "//tensorflow/compiler/mlir/tensorflow:translate_lib",
        "//tensorflow/compiler/mlir/tensorflow:translate_registration",
        "//tensorflow/compiler/mlir/tensorflow:translate_tf_dialect_op",
        "//tensorflow/compiler/mlir/xla:xla_mlir_translate",
        "//tensorflow/core:protos_all_proto_cc",
        "//tensorflow/stream_executor/lib",
        "@llvm//:support",
        "@local_config_mlir//:IR",
        "@local_config_mlir//:Translation",
        "@local_config_mlir//:tools/mlir-translate/mlir-translate",
    ],
)

filegroup(
    name = "litfiles",
    srcs = glob(["runlit*py"]),
)
