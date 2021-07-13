# Setup

```bash
mkdir -p ~/src/cjworkbench
git clone git@github.com:CJWorkbench/cjworkbench.git
git clone git@github.com:CJWorkbench/cjworkbench-deploy.git
git clone git@github.com:meedan/cjworkbench-meedan.git
# ... and set up kubectl to connect to our cluster
```

# To deploy Workbench version `SHA1`

```bash
kubectl config use-context CONTEXT  # e.g., adam@workbench.us-east-1.eksctl.io
cd ~/src/cjworkbench/cjworkbench-deploy
OVERLAY=../cjworkbench-meedan/meedan ./advanced-deploy workbench.us-east-1.eksctl.io SHA1
# advanced-deploy modifies the repositories. Sigh.
git reset --hard
(cd ../cjworkbench-meedan && git reset -hard)
```
