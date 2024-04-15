# Openshift IaC

## Instalação do Argo CD com Helm

Instalação do Argo CD:

```bash
helm upgrade --install argo-cd argo-cd \
    -n argo-cd --create-namespace \
    --repo=https://argoproj.github.io/argo-helm \
    --version=6.7.10 \
    -f https://raw.githubusercontent.com/mmmarceleza/openshift-iac/main/argocd/values.yaml
```

## Instalação das aplicações do repositório

```bash
kubectl apply -f https://raw.githubusercontent.com/mmmarceleza/openshift-iac/main/clusters/ocp-hml/ocp-hml-application.yaml
```
