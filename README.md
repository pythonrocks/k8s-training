# k8s-training
k8s training course


HPA1
---
▶ kubectl -nhpa1 get hpa
NAME   REFERENCE         TARGETS    MINPODS   MAXPODS   REPLICAS   AGE
hpa1   Deployment/hpa1   373%/50%   1         3         1          106s

▶ kubectl -nhpa1 describe hpa hpa1
Name:                     hpa1
Namespace:                hpa1
Labels:                   <none>
Annotations:              autoscaling.alpha.kubernetes.io/conditions:
                            [{"type":"AbleToScale","status":"True","lastTransitionTime":"2020-05-04T15:43:03Z","reason":"ReadyForNewScale","message":"recommended size...
                          autoscaling.alpha.kubernetes.io/current-metrics:
                            [{"type":"Resource","resource":{"name":"cpu","currentAverageUtilization":373,"currentAverageValue":"933m"}}]
CreationTimestamp:        Mon, 04 May 2020 18:42:47 +0300
Reference:                Deployment/hpa1
Target CPU utilization:   50%
Current CPU utilization:  373%
Min replicas:             1
Max replicas:             3
Deployment pods:          3 current / 3 desired
Events:
  Type     Reason                        Age                 From                       Message
  ----     ------                        ----                ----                       -------
  Warning  FailedGetResourceMetric       88s                 horizontal-pod-autoscaler  did not receive metrics for any ready pods
  Warning  FailedComputeMetricsReplicas  88s                 horizontal-pod-autoscaler  failed to get cpu utilization: did not receive metrics for any ready pods
  Warning  FailedGetResourceMetric       42s (x4 over 103s)  horizontal-pod-autoscaler  unable to get metrics for resource cpu: no metrics returned from resource metrics API
  Warning  FailedComputeMetricsReplicas  42s (x4 over 103s)  horizontal-pod-autoscaler  failed to get cpu utilization: unable to get metrics for resource cpu: no metrics returned from resource metrics API
  Normal   SuccessfulRescale             27s                 horizontal-pod-autoscaler  New size: 3; reason: cpu resource utilization (percentage of request) above target


HPA2
---
▶ kubectl -nhpa2 get hpa
NAME   REFERENCE         TARGETS    MINPODS   MAXPODS   REPLICAS   AGE
hpa2   ReplicaSet/hpa2   369%/50%   1         3         3          5m17s

▶ kubectl -nhpa2 describe hpa hpa2
Name:                     hpa2
Namespace:                hpa2
Labels:                   <none>
Annotations:              autoscaling.alpha.kubernetes.io/conditions:
                            [{"type":"AbleToScale","status":"True","lastTransitionTime":"2020-05-04T15:51:47Z","reason":"SucceededRescale","message":"the HPA controll...
                          autoscaling.alpha.kubernetes.io/current-metrics:
                            [{"type":"Resource","resource":{"name":"cpu","currentAverageUtilization":369,"currentAverageValue":"923m"}}]
CreationTimestamp:        Mon, 04 May 2020 18:46:46 +0300
Reference:                ReplicaSet/hpa2
Target CPU utilization:   50%
Current CPU utilization:  369%
Min replicas:             1
Max replicas:             3
ReplicaSet pods:          1 current / 3 desired
Events:
  Type     Reason             Age                   From                       Message
  ----     ------             ----                  ----                       -------
  Normal   SuccessfulRescale  11s                   horizontal-pod-autoscaler  New size: 3; reason: cpu resource utilization (percentage of request) above target

HPA3
---
▶ kubectl -nhpa3 get hpa
NAME   REFERENCE          TARGETS    MINPODS   MAXPODS   REPLICAS   AGE
hpa3   StatefulSet/hpa3   376%/50%   1         3         3          72s

▶ kubectl -nhpa3 describe hpa hpa3
Name:                     hpa3
Namespace:                hpa3
Labels:                   <none>
Annotations:              autoscaling.alpha.kubernetes.io/conditions:
                            [{"type":"AbleToScale","status":"True","lastTransitionTime":"2020-05-04T15:56:06Z","reason":"ReadyForNewScale","message":"recommended size...
                          autoscaling.alpha.kubernetes.io/current-metrics:
                            [{"type":"Resource","resource":{"name":"cpu","currentAverageUtilization":376,"currentAverageValue":"941m"}}]
CreationTimestamp:        Mon, 04 May 2020 18:55:51 +0300
Reference:                StatefulSet/hpa3
Target CPU utilization:   50%
Current CPU utilization:  376%
Min replicas:             1
Max replicas:             3
StatefulSet pods:         3 current / 3 desired
Events:
  Type     Reason                        Age                From                       Message
  ----     ------                        ----               ----                       -------
  Warning  FailedGetResourceMetric       61s (x2 over 77s)  horizontal-pod-autoscaler  did not receive metrics for any ready pods
  Warning  FailedComputeMetricsReplicas  61s (x2 over 77s)  horizontal-pod-autoscaler  failed to get cpu utilization: did not receive metrics for any ready pods
  Normal   SuccessfulRescale             46s                horizontal-pod-autoscaler  New size: 3; reason: cpu resource utilization (percentage of request) above target
