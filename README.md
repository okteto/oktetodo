Now we want to package the application as a Helm chart.

Helm install command:
```
helm upgrade --install db db/chart 
helm upgrade --install server server/chart 
helm upgrade --install client client/chart 
```