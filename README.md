# KinD Cluster Buildkite Plugin

This plugin allows for creation and configuration of a KinD cluster within a Builkite pipeline.

# Options

* k8s_version: The major and minor release of K8S that you would like to target (i.e. v1.29, v1.28, etc.). Default (`v1.29`)
* custom_image: The repository location of a KinD node image that you would like to use rather than the standard published versions from the KinD project (ex: quay.io/myorg/mynodeimage:v1.0.0). This will take priority over `k8s_version`.
* kind_version: The version of the KinD binary you would like to use. Defaults to `v0.21.0`.
* helm_version: The version of the Helm binary you would like to install. Defaults to `v3.14.0`.
* config_path: A path within your codebase that contains a KinD configuration file.
* debug_plugin: Whether to add verbosity to the logging of the plugin itself. This sets the `-x` flag within the plugin to show what commands are being run.

# Usage

```sh
steps:
  - label: ":k8s: Get Pods"
    command: "kubectl get pods"
    plugins:
    - ssh://git@github.com/grid-x/kind-cluster-buildkite-plugin#v0.2.0:
        k8s_version: "1.29"
        config_path: ./config/my-config.yml
```

**Note:** It's important that the k8s_version is in quotes so that it is evaluated appropriately.
