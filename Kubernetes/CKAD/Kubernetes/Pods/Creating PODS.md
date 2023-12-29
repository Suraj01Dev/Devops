## `YAML` Template for creating PODS

```yaml

apiVersion: v1
kind: Pod
metadata:
	name: myapp-pod
	labels: 
		app: my-app
		type: frontend


spec:
	containers:
		- name: nginx-controller
		  image: nginx

```

## Commands related to PODS

- #### Creating a pod
```bash
kubectl run webapp --image nginx
```

- #### Creating pod with YAML
```bash
kubectl apply -f pods.yaml
```

- #### Displaying the metadata of the pods
```bash
kubectl describe po
```

Describing a certain pod
```bash
kubectl describe po webapp
```

- #### Deleting a pod
```bash
kubectl delete po webapp
```

