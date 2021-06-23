workspace(name = "rules_proto_grpc")

load("//:repositories.bzl", "rules_proto_grpc_repos", "rules_proto_grpc_toolchains")

#
# Toolchains
#

rules_proto_grpc_toolchains()

#
# Core
#

rules_proto_grpc_repos()

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()

#
# Android
#
load("//android:repositories.bzl", "android_repos")

android_repos()

load("@rules_jvm_external//:defs.bzl", "maven_install")
load("@io_grpc_grpc_java//:repositories.bzl", "IO_GRPC_GRPC_JAVA_ARTIFACTS", "IO_GRPC_GRPC_JAVA_OVERRIDE_TARGETS", "grpc_java_repositories")

maven_install(
    artifacts = IO_GRPC_GRPC_JAVA_ARTIFACTS,
    generate_compat_repositories = True,
    override_targets = IO_GRPC_GRPC_JAVA_OVERRIDE_TARGETS,
    repositories = [
        "https://repo.maven.apache.org/maven2/",
    ],
)

load("@maven//:compat.bzl", "compat_repositories")

compat_repositories()

grpc_java_repositories()

load("@build_bazel_rules_android//android:sdk_repository.bzl", "android_sdk_repository")

android_sdk_repository(name = "androidsdk")

#
# Buf
#
load("//buf:repositories.bzl", "buf_repos")

buf_repos()

#
# Go
#
# Load rules_go before running grpc_deps in C++, since that depends on a very old version of
# rules_go
#
load("//:repositories.bzl", "bazel_gazelle", "io_bazel_rules_go")  # buildifier: disable=same-origin-load

io_bazel_rules_go()

bazel_gazelle()

load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")

go_rules_dependencies()

go_register_toolchains(
    version = "1.15.8",
)

load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies")

gazelle_dependencies()

load("//go:repositories.bzl", "go_repos")

go_repos()

#
# C++
#
load("//cpp:repositories.bzl", "cpp_repos")

cpp_repos()

load("@com_github_urfave_cli",
    commit = "44cb242eeb4d76cc813fdc69ba5c4b224677e799",
    importpath = "github.com/urfave/cli",
)


#
# KDB+ q 
#
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "protobufkdb",
    urls = ["https://github.com/KxSystems/protobufkdb/archive/refs/tags/1.0.0.zip"],
    sha256 = "...",
)


# local_repository(
#     name = "rules_proto_grpc",
#     path = "../../../",
# )

load("@rules_proto_grpc//:repositories.bzl", "rules_proto_grpc_repos", "rules_proto_grpc_toolchains")

rules_proto_grpc_toolchains()

rules_proto_grpc_repos()

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()

load("@rules_proto_grpc//cpp:repositories.bzl", rules_proto_grpc_cpp_repos = "cpp_repos")

rules_proto_grpc_cpp_repos()

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")

grpc_deps()












