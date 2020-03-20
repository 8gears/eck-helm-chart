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

| Parameter                         | Description                                                                                                              | Default   |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | --------- |
| elasticsearch.enabled             | Create a Elasticsearch Instance                                                                                          | false     |
|                                   | elasticsearch.name                                                                                                       |           | {} |
| elasticsearch.version             |                                                                                                                          | 7.6.1     |
| elasticsearch.nodeSets            | NodeSets allow specifying groups of Elasticsearch nodes sharing the same configuration and Pod templates. See: [Ref.][1] | [Ref.][2] |
| elasticsearch.podDisruptionBudget |                                                                                                                          | {}        |
| elasticsearch.secureSettings      |                                                                                                                          | {}        |
| elasticsearch.updateStrategy      |                                                                                                                          | {}        |

### Kibana CR

| Parameter      | Description              | Default |
| -------------- | ------------------------ | ------- |
| kibana.enabled | Create a Kibana Instance | true    |
|                |

[1]: https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-orchestration.html
[2]: link-to-values-yaml

## Verify

You can use the default Helmfile

```sh
helmfile sync
```
