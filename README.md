# Mothership Helm Charts

Repository for Mothership helm charts.

## Add our repository

```
helm repo add mothership https://mothership.github.io/helm-charts/ 
helm repo update
```

## Releasing

To release a new version, increment the tag in the Chart.yaml, once this lands on
the default branch, a GitHub Action will take care of creating the tag.
