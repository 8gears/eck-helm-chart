# Elastic Cloud on Kubernetes (ECK) Helm Chart

This Helm Chart basically wraps the [Elastic Cloud on Kubernetes (ECK)](https://www.elastic.co/guide/en/cloud-on-k8s/1.0/k8s-overview.html) CRD to make it accessible for Helm only setups avoiding `kubectl` commands.

## Installing the CRD Chart

```sh
helm repo add eck git+https://github.com/8gears/elastic-cloud-on-kubernetes-crd
```

```sh
helm install eck/eck-crd
```

## Installing the CR Chart

```sh
helm repo add eck git+https://github.com/8gears/elastic-cloud-on-kubernetes-crd
```

```sh
helm install eck/eck-crd
```

## ECK CRD - Custom Resource Definition

There are no configuration options for the CRD only for the instances.

## ECK CR - Custom Resources

### Elasticsearch CR

| Parameter                         | Description                                                                                                                                                                                                                                                      | Default          |
| ---                               | ---                                                                                                                                                                                                                                                              | ---              |
| elasticsearch.enabled             | Create a Elasticsearch Instance                                                                                                                                                                                                                                  | true             |
| elasticsearch.version             | Version of Elasticsearch.                                                                                                                                                                                                                                        | 7.6.1            |
| elasticsearch.http                | HTTP holds HTTP layer settings for Elasticsearch.                                                                                                                                                                                                                | {}               |
| elasticsearch.nodeSets            | NodeSets allow specifying groups of Elasticsearch nodes sharing the same configuration and Pod templates. See: [Ref.][1]                                                                                                                                         | [values.yaml][2] |
| elasticsearch.podDisruptionBudget | PodDisruptionBudget provides access to the default pod disruption budget for the Elasticsearch cluster. <br>The default budget selects all cluster pods and sets `maxUnavailable` to 1. To disable, set `PodDisruptionBudget` to the empty value (`{}` in YAML). | {}               |
| elasticsearch.secureSettings      | SecureSettings is a list of references to Kubernetes secrets containing sensitive configuration options for Elasticsearch. See [Ref.][3]                                                                                                                         | {}               |
| elasticsearch.updateStrategy      | UpdateStrategy specifies how updates to the cluster should be performed.                                                                                                                                                                                         | {}               |

[1]: https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-orchestration.html
[2]: https://github.com/8gears/eck-helm-chart/blob/master/eck-cr/values.yaml#L10  
[3]: https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-es-secure-settings.html

### Kibana CR

| Parameter               | Description                                                                                                                        | Default |
| ---                     | ---                                                                                                                                | ---     |
| kibana.enabled          | Create a Kibana Instance                                                                                                           | true    |
| kibana.version          | Version of Kibana.                                                                                                                 | 7.6.1   |
| kibana.http             | HTTP holds the HTTP layer configuration for Kibana.                                                                                | {}      |
| kibana.image            | Image is the Kibana Docker image to deploy.                                                                                        | {}      |
| kibana.count            | Count of Kibana instances to deploy.                                                                                               | {}      |
| kibana.config           | Config holds the Kibana configuration. See [Ref][21]                                                                               | {}      |
| kibana.elasticsearchRef | ElasticsearchRef is a reference to an Elasticsearch cluster running in the same Kubernetes cluster.                                | {}      |
| kibana.podTemplate      | PodTemplate provides customisation options (labels, annotations, affinity rules, resource requests, and so on) for the Kibana pods | {}      |
| kibana.secureSettings   | SecureSettings is a list of references to Kubernetes secrets containing sensitive configuration options for Kibana. See [Ref][22]  | {}      |

[21]: https://www.elastic.co/guide/en/kibana/current/settings.html 
[22]: https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-kibana.html#k8s-kibana-secure-settings


## Example


## Verify Installation

You can use the default Helmfile

```sh
helmfile sync
```
