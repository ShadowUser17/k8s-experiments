#### HPA for service metric:
```yaml
apiVersion: "autoscaling/v2"
kind: "HorizontalPodAutoscaler"
metadata:
  name: "testing-app"
  namespace: "testing"
spec:
  scaleTargetRef:
    apiVersion: "apps/v1"
    kind: "Deployment"
    name: "testing-app"
  minReplicas: 1
  maxReplicas: 5
  metrics:
    - type: "Object"
      object:
        describedObject:
          apiVersion: "v1"
          kind: "Service"
          name: "testing-app"
        metric:
          name: "ingress_requests_total"
        target:
          type: "Value"
          value: "10"
  behavior:
    scaleDown:
      stabilizationWindowSeconds: 60
```

#### HPA for pod metric:
```yaml
apiVersion: "autoscaling/v2"
kind: "HorizontalPodAutoscaler"
metadata:
  name: "testing-app"
  namespace: "testing"
spec:
  scaleTargetRef:
    apiVersion: "apps/v1"
    kind: "Deployment"
    name: "testing-app"
  minReplicas: 1
  maxReplicas: 5
  metrics:
    - type: "Pods"
      pods:
        metric:
          name: "server_connections_total"
        target:
          type: "AverageValue"
          averageValue: "10"
  behavior:
    scaleDown:
      stabilizationWindowSeconds: 60
```
