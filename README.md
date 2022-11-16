# Helm Repository for Helm Charts

This repository will hold Helm Charts that hopefully someone will deem useful.

## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

  helm repo add bkkas <https://bkkas.github.io/helm-charts>

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run `helm search repo
bkkas` to see the charts.

To install the `<chart-name>` chart:

    helm install my-<chart-name> <alias>/<chart-name>

To uninstall the chart:

    helm delete my-<chart-name>

## Lint of charts

There is a github action that run chart lint.

Helm Chart needs the CRD from these installed:

```yaml
  dependencies:
    - name: aad-pod-identity
      version: 4.1.13
      repository: https://raw.githubusercontent.com/Azure/aad-pod-identity/master/charts
    - name: csi-secrets-store-provider-azure
      version: 1.3.0
      repository: https://azure.github.io/secrets-store-csi-driver-provider-azure/charts
```

The flux image controller CRD is also needed.
