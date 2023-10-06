### README for challenge Helm chart values.yaml in Markdown

| Value | Description | Default |
|---|---|---|
| `replicaCount` | The number of replicas to deploy. | 1 |
| `image.repository` | The name of the Docker image repository. | nginx |
| `image.pullPolicy` | The pull policy for the Docker image. | IfNotPresent |
| `image.tag` | The tag of the Docker image to use. | The chart's appVersion |
| `imagePullSecrets` | A list of image pull secrets to use when pulling the Docker image. | [] |
| `nameOverride` | An override for the name of the Deployment and Service resources. | None |
| `fullnameOverride` | An override for the fullname of the Deployment and Service resources. | None |
| `serviceAccount.create` | Whether to create a ServiceAccount for the Deployment. | True |
| `serviceAccount.automount` | Whether to automatically mount the ServiceAccount's API credentials into the Deployment's pods. | True |
| `serviceAccount.annotations` | A map of annotations to add to the ServiceAccount. | {} |
| `serviceAccount.name` | The name of the ServiceAccount to use. If not set and create is true, a name will be generated using the fullname template. | None |
| `podAnnotations` | A map of annotations to add to the Deployment's pods. | {} |
| `podLabels` | A map of labels to add to the Deployment's pods. | {} |
| `podSecurityContext` | A PodSecurityContext object to apply to the Deployment's pods. | {} |
| `securityContext` | A SecurityContext object to apply to the Deployment's pods. | {} |
| `service.type` | The type of Service to create. | ClusterIP |
| `service.port` | The port to expose the Deployment on. | 22 |
| `ingress.enabled` | Whether to create an Ingress resource for the Service. | False |
| `ingress.className` | The name of the IngressClass to use. | None |
| `ingress.annotations` | A map of annotations to add to the Ingress resource. | {} |
| `ingress.hosts` | A list of hosts to map to the Service. Each host should have a `path` and `pathType` property. | [] |
| `ingress.tls` | A list of TLS secrets to use for the Ingress resource. Each secret should have a `secretName` and `hosts` property. | [] |
| `resources` | A map of resource requests and limits to apply to the Deployment's pods. | {} |
| `autoscaling.enabled` | Whether to enable autoscaling for the Deployment. | False |
| `autoscaling.minReplicas` | The minimum number of replicas to maintain. | 1 |
| `autoscaling.maxReplicas` | The maximum number of replicas to scale up to. | 100 |
| `autoscaling.targetCPUUtilizationPercentage` | The target CPU utilization percentage for the Deployment. | 80 |
| `autoscaling.targetMemoryUtilizationPercentage` | The target memory utilization percentage for the Deployment. | 80 |
| `volumes` | A list of additional volumes to mount into the Deployment's pods. | [] |
| `volumeMounts` | A list of additional volume mounts to apply to the Deployment's pods. | [] |
| `nodeSelector` | A map of node labels to match when scheduling the Deployment's pods. | {} |
| `tolerations` | A list of tolerations to apply to the Deployment's pods. | [] |
| `affinity` | An Affinity object to apply to the Deployment's pods. | {} |
| `authorized_keys` | A map of authorized keys to add to the Deployment's pods. The keys should be in the format `username:key`. | {} |

**Additional notes:**

* The `authorized_keys` map is added to the Deployment's pods using a Kubernetes ConfigMap. The ConfigMap is created with the name `challenge-authorized-keys`.
* The Deployment's pods are configured to use the `challenge-authorized-keys` ConfigMap as a read-only volume.