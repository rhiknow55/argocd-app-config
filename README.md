# argocd-app-config
Following along ArgoCD Tutorial by TechWorld with Nana


# Commands
`minikube start --driver docker`
`minikube status`

`kubectl create namespace argocd`
`kubectl create ns argocd`

`kubectl get ns` (namespace)

`kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`
- creates a bunch of components

### Wait for pods to be created
`kubectl get pod -n argocd -w` The -w flag waits

### How to delete all to restart
`kubectl delete --all deployments -n argocd`
`kubectl delete --all pods -n argocd`
`kubectl delete namespace argocd`

`kubectl get pods -n argocd` to check
`kubectl get ns` to check


### Port forward (in order to access ArgoCD UI)
`kubectl port-forward -n argocd svc/argocd-server 8080:443`

username = admin
password = <auto generated>

### Get password to log in (https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli)
`kubectl -n argocd get secret argocd-initial-admin-secret -o yaml`

`echo <encoded password> | base64 --decode`


### How automatic updates work
ArgoCD polls the git repo every 3 minutes
you can also set up webhook instead
