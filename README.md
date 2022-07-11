# Floripa Tech Day - 2022

Este repositório contém os manifestos utilizados na apresentação.

## Apresentação:

[![Slides](slides.png)](https://www.canva.com/design/DAFFjQG1wDs/CDrxfeVx9TZ9wsDPdU2Ofw/view)


| Path | Application | Description |
|------|-------------|-------------|
| [app](app-of-apps/) | App of Apps | Manifesto principal que contempla todos os demais recursos/manifestos que serão aplicados no cluster |
| [conf](conf/) | Apps Manifests | Definição dos manifestos que serão utilizados pelo App of Apps |
| [ingress-nginx](nginx-ingress/) | NGINX Ingress | Manifesto para instalação do NGINX ingress controller |


## Requisitos:

- Um cluster [Kubernetes](https://kubernetes.io/) local ou na núvem.
- Instalar o [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) no cluster.


### instalar o ArgoCD no k8s

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### access ArgoCD UI

```bash
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd
```

### logar como admin no ArgoCD com o Token criado na instalação

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo
```

#### apply de application configuration

```bash
kubectl apply -f app/app-of-apps.yaml
```
