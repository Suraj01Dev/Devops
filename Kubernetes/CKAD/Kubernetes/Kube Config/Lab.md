
#### Task 1
Create a new context with the name `mininew` by the editing the `kubeconfig` file with the `namespace` name `dev`.

**Soln**

Steps :
1. Take a backup of the current config file (~/.kube/config) -> config.bak
2. Copy the contents of the current config.bak file into a new config file.

```
apiVersion: v1
clusters:
- cluster:
    certificate-authority: /home/suraj-14258/.minikube/ca.crt
    server: https://192.168.39.251:8443
  name: minikube
  
contexts:
- context:
    cluster: minikube
    namespace: default
    user: minikube
  name: minikube
current-context: minikube

kind: Config
preferences: {}

users:
- name: minikube
  user:
    client-certificate: /home/suraj-14258/.minikube/profiles/minikube/client.crt
    client-key: /home/suraj-14258/.minikube/profiles/minikube/client.key

```

The above is the default contents of default config file.

As we know that the kubeconfig has 3 important parts to its config file, which is clusters, contexts and users.

And the contexts is the part which connects the users with the clusters.

```
- context:
    cluster: minikube
    namespace: default
    user: minikube
  name: minikube
current-context: minikube
```

In this example the context `minikube` connects the user `minikube` with the namespace minikube. **Our task is to create a new context `mininew` with namespace `dev` .


```
- context:
    cluster: minikube
    namespace: default
    user: minikube
  name: minikube
- context:
    cluster: minikube
    namespace: dev
    user: minikube
  name: mininew
current-context: mininew
```

Now after making the above changes executing the below commands will display the lists of contexts available and the current context.

```
kubectl config get-contexts
```

```
kubectl config current-context
```
