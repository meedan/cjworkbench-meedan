# Prerequisites

Install kustomize:
```bash
curl --silent --location --remote-name \
"https://github.com/kubernetes-sigs/kustomize/releases/download/kustomize/v3.2.3/kustomize_kustomize.v3.2.3_linux_amd64" && \
chmod a+x kustomize_kustomize.v3.2.3_linux_amd64 && \
sudo mv kustomize_kustomize.v3.2.3_linux_amd64 /usr/local/bin/kustomize
```

Create cluster:
```bash
eksctl create cluster \
  --name workbench \
  --region eu-west-1 \
  --with-oidc \
  --ssh-access \
  --ssh-public-key workbench-eks
```

Enable logging:
```bash
eksctl utils update-cluster-logging \
  --cluster=workbench \
  --region=eu-west-1 \
  --enable-types=all 
```

# Setup

```bash
git clone git@github.com:CJWorkbench/cjworkbench.git
# NOTE: the following meedan repository incorporates the cjworkbench-deploy scripts.
git clone git@github.com:meedan/cjworkbench-meedan.git
cd cjworkbench-meedan
# ... and set up kubectl to connect to our cluster
```

# Deploy cluster

```bash
cd cluster-setup/aws
./cluster-setup.sh
cd -
```

# To deploy Workbench version `SHA1` from ECR

```bash
kubectl config use-context CONTEXT  # e.g., sysops@workbench.eu-west-1.eksctl.io
OVERLAY=./meedan ./advanced-deploy SHA1
```
