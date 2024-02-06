
# Meta Github Action Self Hosted Runner 

## Self Hosted DIND Runners : 

This is running under `actions-runner-system` namespace with EKS Cluster 

Kubectl Commands to Setup this 

```
1. kubectl create ns actions-runner-system 
    This command to create initial namespace, which will contain all resources for github action runnners.

2. kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.8.2/cert-manager.yaml
    Cert-manager adds certificates and certificate issuers as resource types in Kubernetes clusters, and simplifies the process of obtaining, renewing and using those certificates.

3. kubectl create secret generic controller-manager  -n actions-runner-system --from-literal=github_token=<GITHUB TOKEN>
    Configure Personal Access Token.

4. kubectl get secret -n actions-runner-system 
    Used to confirm if secret has been craeted.

5. kubectl apply -f https://github.com/actions/actions-runner-controller/releases/download/v0.22.0/actions-runner-controller.yaml
    Deploy ARC

6. kubectl apply -f dindrunnerdeployment.yaml

7. kubectl get pods --namespace actions-runner-system

Now you will be able to see self hosted runners running in K8s.

```

Reference : https://github.com/actions/actions-runner-controller/blob/master/docs/quickstart.md 


