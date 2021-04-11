# Setup

`kind create tekton`

`kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml`

Install CLI
```
brew tap tektoncd/tools
brew install tektoncd/tools/tektoncd-cli
```

Build image:
`docker build gh-image --tag github-cli`

