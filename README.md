# Setup

```bash
git clone git@github.com:CJWorkbench/cjworkbench.git
# NOTE: the following meedan repository incorporates the cjworkbench-deploy scripts.
git clone git@github.com:meedan/cjworkbench-meedan.git
cd cjworkbench-meedan
# ... and set up kubectl to connect to our cluster
```

# To deploy Workbench version `SHA1` from ECR

```bash
kubectl config use-context CONTEXT  # e.g., sysops@workbench.us-east-1.eksctl.io
OVERLAY=./meedan ./advanced-deploy workbench.eu-west-1.eksctl.io SHA1
```
