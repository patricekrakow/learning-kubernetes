## Kafka simple logging demontration

```
$ touch counter.pod.yaml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: counter
spec:
  containers:
  - name: count
    image: busybox
    args: [/bin/sh, -c,
            'i=0; while true; do echo "$i: $(date)"; i=$((i+1)); sleep 1; done']
```

```
$ kubectl apply -f counter.pod.yaml
pod/counter created
```

```
$ kubectl get pods
NAME      READY   STATUS    RESTARTS   AGE
counter   1/1     Running   0          83s
```

```
$ kubectl logs counter
0: Wed May  6 09:00:08 UTC 2020
1: Wed May  6 09:00:09 UTC 2020
2: Wed May  6 09:00:10 UTC 2020
3: Wed May  6 09:00:11 UTC 2020
...
```

```
$ kubectl delete pod counter
pod "counter" deleted
```

> <https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#logs>
