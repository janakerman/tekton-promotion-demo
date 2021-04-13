# Setup

Install CLI:
```
brew tap tektoncd/tools
brew install tektoncd/tools/tektoncd-cli
```

Start a new Kind cluster with a local registry:
`./kind-create.sh tekton`

Install Tekton:
```
kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
```

Build images:
```
docker build gh-cli --tag localhost:5000/github-cli
docker push localhost:5000/github-cli
```

Install tasks:
```
kubectl apply -f task-git-clone.yaml
kubectl apply -f task-promote.yaml
kubectl apply -f sources-pvc.yaml
kubectl apply -f pipeline.yaml
```
```
kubectl delete -f task-git-clone.yaml
kubectl delete -f task-promote.yaml
kubectl delete -f sources-pvc.yaml
kubectl delete -f pipeline.yaml
```

Create github token secret:
```
kubectl create secret generic github-token --from-literal=bot-token=$GITHUB_TOKEN
```

Run the pipeline:
```
kubectl apply -f pipeline-run.yaml
```


