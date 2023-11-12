```
helm -n cass-operator diff upgrade --install \
    --set server.replicaCount=1 \
    --set cassandra.config.cluster_size=1 \
    --set prometheus.enabled=false \
    --set grafana.enabled=false \
    --set elasticsearch.enabled=false \
    temporal-minimum . -f values.yaml
```
- Support for Cassandra as a Visibility database is deprecated beginning with Temporal Server v1.21
- Advance Visibility support: https://docs.temporal.io/cluster-deployment-guide#supported-databases
- Revert https://github.com/temporalio/helm-charts/pull/251
- Remove Cassandra Dependency
- Decision: Use Postgres as Visibility store: https://docs.temporal.io/cluster-deployment-guide#postgresql
- Use SecretTplEnv placeholder