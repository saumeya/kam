## Contribution and developing locally

1.For allowing our local UI development environment to connect to the gitops backend, we need to expose our backend using a route. Create a cluster route file `cluster-route.yaml` and add the following route to it
```
kind: Route
apiVersion: route.openshift.io/v1
metadata:
  name: cluster
  namespace: openshift-gitops  
spec: 
  to: 
    kind: Service
    name: cluster   
  port:
    targetPort: 8080
  tls:
    termination: reencrypt
    insecureEdgeTerminationPolicy: Allow
```    
2. Run `oc apply -f cluster-route.yaml` this will create a route that connects to the backend

3. Now continue to locally run dev console 