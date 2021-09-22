# rds-auth-proxy

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.0.1](https://img.shields.io/badge/AppVersion-0.0.1-informational?style=flat-square)

A two-layer proxy for connecting into RDS postgres databases based on IAM authentication.

**Homepage:** <https://github.com/mothership/rds-auth-proxy>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Jack Wink |  | https://github.com/mothership/rds-auth-proxy/issues |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| deployment | object | `{"affinity":{},"image":{"pullPolicy":"IfNotPresent","pullSecrets":[],"repository":"ghcr.io/mothership/rds-auth-proxy:0.0.1"},"nodeSelector":{},"podSecurityContext":{},"replicaCount":1,"resources":{},"securityContext":{},"tolerations":[]}` | Deployment resource settings  |
| deployment.affinity | object | `{}` | Affinity rules for the proxy deployment  |
| deployment.image.pullPolicy | string | `"IfNotPresent"` | Image pull policy for the proxy  |
| deployment.image.pullSecrets | list | `[]` | Image pull policy for the proxy deployment  |
| deployment.image.repository | string | `"ghcr.io/mothership/rds-auth-proxy:0.0.1"` | If you want to bundle your own proxy distribution, you can change the image/tag  |
| deployment.nodeSelector | object | `{}` | Node selector, if you want to deploy it to a particular node group |
| deployment.podSecurityContext | object | `{}` | Pod security context  |
| deployment.replicaCount | int | `1` | Number of pods to run |
| deployment.resources | object | `{}` | Resources for the proxy deployment  |
| deployment.securityContext | object | `{}` | Container security context for the proxy  |
| deployment.tolerations | list | `[]` | Tolerations for the proxy deployment  |
| fullnameOverride | string | `""` |  |
| nameOverride | string | `""` |  |
| proxy | object | `{"allowedRDSTags":[],"blockedRDSTags":[],"certManager":{"enabled":true},"ssl":{"certificatePath":"","clientCertificatePath":"","clientPrivateKey":"","enabled":true,"keyPath":""},"targets":{}}` | Settings for the proxy itself |
| proxy.allowedRDSTags | list | `[]` | Tags used to filter RDS instances. If empty, all RDS postgres instances are allowed to connect through the proxy unless otherwise blocked.  If multiple tags are set, allowed tags must be on  the RDS instance, and their values must match the value exactly. |
| proxy.blockedRDSTags | list | `[]` | Tags used to filter RDS instances. If empty, all RDS postgres instances are allowed to connect  through the proxy. If multiple tags are set, ANY matching tag on the RDS instance will stop the proxy connecting to it. |
| proxy.certManager | object | `{"enabled":true}` | Set to false if you want to bring your own certificate  |
| proxy.certManager.enabled | bool | `true` | If true, creates client SSL certificates using certManager. Client certificates are  used in the sessions with RDS instances. If proxy.ssl.enabled is also true, this will  issue a self-signed certificate for communication between clients and the proxy server.  |
| proxy.ssl | object | `{"certificatePath":"","clientCertificatePath":"","clientPrivateKey":"","enabled":true,"keyPath":""}` | The SSL config for the proxy itself. SSL for individual  hosts/targets is defined below |
| proxy.ssl.certificatePath | string | `""` | Path in the container to the proxy's SSL certificate, if proxy.certManager.enabled is true, this is ignored. |
| proxy.ssl.clientCertificatePath | string | `""` | Path in the container to the SSL certificate for outbound connections to RDS. if proxy.certManager.enabled is true, this is ignored. |
| proxy.ssl.clientPrivateKey | string | `""` | Path in the container to the SSL private key for outbound connections to RDS.  If proxy.certManager.enabled is true, this is ignored. |
| proxy.ssl.enabled | bool | `true` | If true, the proxy will enable clients to use SSL when connecting to it |
| proxy.ssl.keyPath | string | `""` | Path in the container to the proxy's SSL private key, if proxy.certManager.enabled is true, this is ignored. |
| proxy.targets | object | `{}` | ({ "name": { "host": string, "ssl": { "mode": "disable" }}}) Additional databases that you want the proxy to allow connections to, like self-hosted postgres  instances. |
| serviceAccount | object | `{"annotations":{},"create":true}` | Service account settings if we create the service account  |
| serviceAccount.annotations | object | `{}` | Annotations for the service-account - this can be used for IRSA  auth to AWS |
| serviceAccount.create | bool | `true` | Creates a service account for you if true |
| serviceAccountName | string | `""` | Service account name for the proxy deployment, if you own service-account |

