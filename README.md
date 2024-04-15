# Openshift IaC

## Instalação do Argo CD com Helm

```bash
helm upgrade --install argo-cd argo-cd \
    -n argo-cd --create-namespace \
    --repo=https://argoproj.github.io/argo-helm \
    --version=6.7.10 \
    -f values.yaml
```

## Instalação das aplicações do repositório

```bash
kubectl apply -k ./clusters/ocp-hml/
```
