Static configmap.

Base on projects:
* [kube-prometheus-stack](https://github.com/prometheus-community/helm-charts)
* [prometheus-operator](https://github.com/prometheus-operator/kube-prometheus/tree/main/manifests)

```yaml
# prometheus-community/prometheus values

server:
  extraConfigmapMounts:
    - name: rules-configmap
      mountPath: /etc/prometheus-rules
      configMap: prometheus-rules
      readOnly: true

configmapReload:
  prometheus:
    extraVolumeDirs:
      - /etc/prometheus-rules
    extraConfigmapMounts:
      - name: rules-configmap
        mountPath: /etc/prometheus-rules
        configMap: prometheus-rules
        readOnly: true
```