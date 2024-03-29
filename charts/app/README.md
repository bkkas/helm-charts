# app

![Version: 0.5.12](https://img.shields.io/badge/Version-0.5.12-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.0.0](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

A Helm chart for Kubernetes

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| aadpodidentity.akvcsidriver.cloudName | string | `"AzurePublicCloud"` | [OPTIONAL for Azure] if not provided, the Azure environment defaults to AzurePublicCloud |
| aadpodidentity.akvcsidriver.enabled | bool | `false` | Enable or disable Azure Key Vault CSI Driver |
| aadpodidentity.akvcsidriver.keyvaultName | string | `nil` | Set to the name of your key vault |
| aadpodidentity.akvcsidriver.objects | string | `nil` |  |
| aadpodidentity.akvcsidriver.provider | string | `"azure"` |  |
| aadpodidentity.akvcsidriver.secretObjects | string | `nil` |  |
| aadpodidentity.akvcsidriver.tenantId | string | `nil` | The tenant ID of the key vault |
| aadpodidentity.akvcsidriver.usePodIdentity | bool | `true` | Set to true for using aad-pod-identity to access your key vault |
| aadpodidentity.clientID | string | `nil` |  |
| aadpodidentity.enabled | bool | `false` | Enable or disable AAD Pod Identity |
| aadpodidentity.resourceID | string | `nil` |  |
| aadpodidentity.selector | string | `nil` | Use existing AzureIdentityBinding, Will will suppress creation of AadPodIdentity and AzureIdentityBinding |
| aadpodidentity.type | int | `0` | 0 = User Assigned Managed Identity, 1 = Service Principal with client secret, 2 = Service Principal with certificate |
| affinity | Optional | `{"nodeAffinity":{"preferredDuringSchedulingIgnoredDuringExecution":[{"preference":{"matchExpressions":[{"key":"kubernetes.azure.com/mode","operator":"In","values":["User"]}]},"weight":1}]}}` | Affinity rules |
| containerName | string | `nil` | By default `containerName` will be equal to `{{ .Values.namespace }}-{{.Values.name }}` |
| envVars | string | `nil` |  |
| healthEndpoint | REQUIRED | `"/health"` | Set health endpoint |
| healthPort | REQUIRED | `80` | Set health port |
| image.pullPolicy | string | `"IfNotPresent"` | Always, IfNotPresent or Never |
| image.repository | string | `"ubuntu"` |  |
| image.tag | string | `"latest"` |  |
| image.update | object | `{"enabled":false,"filterTags":{"extract":"$ts","pattern":"^dev-[a-fA-F0-9]+-(?P<ts>.*)"},"interval":"1m0s","policy":{"numerical":{"order":"asc"}}}` | Flux Image policy & repository |
| image.update.enabled | REQUIRED | `false` | Enable or disable Flux Image policy |
| image.update.filterTags | object | `{"extract":"$ts","pattern":"^dev-[a-fA-F0-9]+-(?P<ts>.*)"}` | Image policy - https://fluxcd.io/docs/components/image/imagepolicies/ |
| image.update.filterTags.pattern | string | `"^dev-[a-fA-F0-9]+-(?P<ts>.*)"` | ${PREFIX}-${GIT_SHA:0:7}-$(date +%s) |
| image.update.interval | string | `"1m0s"` | Image repository - https://fluxcd.io/docs/components/image/imagerepositories/ |
| ingress.applicationGatewayCertName | string | `nil` | The name of the certificate used on the listener on the application gateway |
| ingress.enabled | bool | `false` | Enable or disable ingress |
| ingress.host | string | `nil` | Set your hostname |
| ingress.http[0].path | string | `"/app/*"` |  |
| ingress.http[0].pathType | string | `"prefix"` |  |
| ingress.http[0].port | int | `80` | Backend port |
| ingress.timeout | int | `30` | Default request timeout https://azure.github.io/application-gateway-kubernetes-ingress/annotations/#request-timeout |
| name | REQUIRED | `"app-name"` | Name your application |
| namespace | REQUIRED | `"app-namespace"` | The namespace the application will be deployed in |
| podLabels | Optional | `[]` | Add pod labels |
| ports | string | `nil` |  |
| readyEndpoint | REQUIRED | `"/health"` | Set ready endpoint |
| readyPort | REQUIRED | `80` | Set ready port |
| replicaCount | int | `1` | Replica count of pods |
| resources.limits | object | `{"cpu":"0.5","memory":"256Mi"}` | Set resource limits |
| resources.requests | object | `{"cpu":"0.25","memory":"128Mi"}` | Set resource requests |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
