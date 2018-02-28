# Using Custom Resource Definitions and Custom Resources in Kubernetes

## Create a CustomResourceDefintion

See [crd.yaml][] for a CRD.  Create it:

```
kubectl -f crd.yaml
```

You can check that the new CRD also created a new namespaces API endpoint at 
`/apis/${group}/${version}/namespaces/*/${plural}` (in this case:
`/apis/stable.example.com/v1/namespaces/*/crontabs`)

```
kubectl proxy &
curl http://127.0.0.1:8001/apis/stable.example/v1/namespaces/*/crontabs
```

```json
{"apiVersion":"stable.example.com/v1","items":[],"kind":"CronTabList","metadata":{"continue":"","resourceVersion":"69668","selfLink":"/apis/stable.example.com/v1/namespaces/*/crontabs"}}
```

- - - - - 

This is based on the K8s official documentation.
