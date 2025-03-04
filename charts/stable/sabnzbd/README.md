# sabnzbd

![Version: 7.0.0](https://img.shields.io/badge/Version-7.0.0-informational?style=flat-square) ![AppVersion: v3.2.1](https://img.shields.io/badge/AppVersion-v3.2.1-informational?style=flat-square)

Free and easy binary newsreader

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://sabnzbd.org/>
* <https://github.com/k8s-at-home/container-images>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 2.3.1 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install sabnzbd k8s-at-home/sabnzbd
```

## Installing the Chart

To install the chart with the release name `sabnzbd`

```console
helm install sabnzbd k8s-at-home/sabnzbd
```

## Uninstalling the Chart

To uninstall the `sabnzbd` deployment

```console
helm uninstall sabnzbd
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install sabnzbd \
  --set env.TZ="America/New York" \
    k8s-at-home/sabnzbd
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install sabnzbd k8s-at-home/sabnzbd -f values.yaml
```

## Custom configuration

**IMPORTANT NOTE:** when installing this chart for the first time you will get the follow message in your browser when trying to access Sabnzbd: `Access denied - Hostname verification failed: sabnzbd.org/hostname-check`

You can do one of two things to solve this issue:

1. Update the `sabnzbd.ini` config file to your `ingress` name and/or `loadBalancerIP` to the `host_whitelist` field and restart the pod, or
2. Forward the service to your local machine with `kubectl port-forward service/sabnzbd -n default 8080:8080` and update the `host_whitelist` in the Sabnzbd Settings UI

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env | object | `{}` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ghcr.io/k8s-at-home/sabnzbd"` |  |
| image.tag | string | `"v3.2.1"` |  |
| ingress.enabled | bool | `false` |  |
| persistence.config.emptyDir.enabled | bool | `false` |  |
| persistence.config.enabled | bool | `false` |  |
| persistence.downloads.emptyDir.enabled | bool | `false` |  |
| persistence.downloads.enabled | bool | `false` |  |
| persistence.downloads.mountPath | string | `"/downloads"` |  |
| persistence.media.emptyDir.enabled | bool | `false` |  |
| persistence.media.enabled | bool | `false` |  |
| persistence.media.mountPath | string | `"/media"` |  |
| service.port.port | int | `8080` |  |
| strategy.type | string | `"Recreate"` |  |

## Changelog

All notable changes to this application Helm chart will be documented in this file but does not include changes from our common library. To read those click [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common#changelog).

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

### [7.0.0]

#### Changed

- **Breaking**: swap linuxserver.io images for k8s@home image

### [1.0.0]

#### Added

- N/A

#### Changed

- N/A

#### Removed

- N/A

[7.0.0]: #7.0.0
[1.0.0]: #1.0.0

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
