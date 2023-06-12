# Hybrid Helm/Golang operator for Backstage prototype

Reconciler logic: https://github.com/operator-framework/helm-operator-plugins/blob/main/pkg/reconciler/reconciler.go
Hybrid operators lacks documentation, see:
- https://github.com/operator-framework/helm-operator-plugins/issues/136
- https://docs.openshift.com/container-platform/4.10/operators/operator_sdk/helm/osdk-hybrid-helm.html


## Known issues

- Before first sync we need to pull `oc get ingresses.config/cluster -o jsonpath={.spec.domain}` data and set as `.global.clusterRouterBase`
- After first sync/install (before any upgrade call or reconcile), we need to set `.upstream.postgresql.auth.existingSecret`
