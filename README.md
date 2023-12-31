# Oktetodo

A todo list application to demonstrate cloud development using Okteto.

## Notes on migrating the app

The application's microservices are packaged as helm charts.

Helm install command:
```
helm upgrade --install db db/chart 
helm upgrade --install server server/chart 
helm upgrade --install client client/chart 
```

Remove the hard coded ingress classname in the `ingress.yaml`. Add the annotation to the ingress to get the endpoints for your application:

```
annotations:
    dev.okteto.com/generate-host: "true"
```
Create the `okteto.yaml`.

To build images locally: `docker build -t rinkiyakedad/oktetodo-client --platform=linux/amd64 .`