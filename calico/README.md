Source: https://docs.tigera.io/calico/3.25/getting-started/kubernetes/flannel/migration-from-flannel#migrate-from-flannel-networking-to-calico-networking-live-migration

# Migrate from flannel networking to Calico networking, live migration
Install Calico.

```
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/flannel-migration/calico.yaml
```

Start the migration controller.
```
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/flannel-migration/migration-job.yaml
```

You will see nodes begin to update one at a time.

Monitor the migration.
```
kubectl get jobs -n kube-system flannel-migration
```
When the host node is upgraded, the migration controller may be rescheduled several times. The installation is complete when the output of the above command shows 1/1 completions. For example:
```
NAME                COMPLETIONS   DURATION   AGE
flannel-migration   1/1           2m59s      5m9s
```
Delete the migration controller.
```
kubectl delete -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/flannel-migration/migration-job.yaml
```

