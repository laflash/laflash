# Helm

See also &lt;?add topic='Helm Templates'?&gt; &lt;?add topic='kubernetes'?&gt; &lt;?add topic='Openshift'?&gt;

## Setup

For instructions check [here](https://docs.helm.sh/using_helm/#quickstart-guide)

```text
helm init   
helm repo update

# To get access to unstable charts
helm repo add incubator https://kubernetes-charts-incubator.storage.googleapis.com/
```

For Openshift there is an [RBAC compatible installation proceduce](https://blog.openshift.com/getting-started-helm-openshift/).

## Setup Troubleshooting

```text
helm init --client-only                      # (Helm 2.x only) do not initialize tiller
helm init --upgrade --service-account tiller # (Helm 2.x only) ensure to sync client/server versions

helm version       # Client/server versions should be equal
```

## List available packages

To list charts \(packages\)

```text
helm search
```

## List installed releases

```text
helm list
helm get values <release>           # Print the values the release was installed with
```

## Install package

Helm 2

```text
helm install <chart> [--namespace <ns>]         # Choose release name for you
helm install --name <name> <chart>              # Install chart as release <name>

helm install ./<chart dir> --namespace <ns>     # Install from local archive
```

Helm 3

```text
helm install <name> <chart> [--namespace <ns>]  # Per-default you need to provide a release name
helm install -g <chart>     [--namespace <ns>]  # Helm 2 like generated release name
```

## Upgrading releases

```text
helm upgrade <name>
helm upgrade --wait <name>                      # Wait for pods to come up
```

## Working with plugins

```text
helm plugin list
helm plugin install <plugin URL>
```

## Creating chart packages

```text
helm create mychart                                    # Create boilerplate

helm install mychart-0.1.0.tgz --dry-run --debug       # Test installing
```

## Best Practices

See [Helm Best Practices](/blog/Helm+Best+Practices)

## Misc

* [https://kubeapps.com/](https://kubeapps.com/): Web GUI for installing Helm charts
* Infrastructure as Code solutions for Helm:
  * [helmfile](https://github.com/roboll/helmfile)
  * [Helmsman](https://github.com/Praqma/helmsman)
  * Terraform
* Solutions to host helm charts yourself:
  * chartmuseum
  * harbour
  * Nexus
  * jFrog Artifactory

