# Openshift IaC

## Instalação do Argo CD com Helm

Criação do namespace para o Argo CD:

```bash
kubectl create ns argo-cd
```

Coleta da ID destinada aos Pods do namespace do Argo CD:

```bash
UID_RANGE=$(kubectl get ns argo-cd -ojsonpath='{.metadata.annotations.openshift\.io\/sa\.scc\.uid-range}' | cut -d / -f 1)
```

Instalação do Argo CD:

```bash
helm upgrade --install argo-cd argo-cd \
    -n argo-cd \
    --repo=https://argoproj.github.io/argo-helm \
    --version=6.7.10 \
    -f argocd/values.yaml \
    --set redis.securityContext.runAsUser="$UID_RANGE" \
    --set redis.securityContext.runAsGroup="$UID_RANGE" \
    --set redis.securityContext.fsGroup="$UID_RANGE"
```

## Instalação das aplicações do repositório

```bash
kubectl apply -f https://raw.githubusercontent.com/mmmarceleza/openshift-iac/main/clusters/ocp-hml/ocp-hml-application.yaml
```
