# gitops_CD_test_project
a continuous deployment simple pipeline using gtihub and argo CD into a microk8s cluster
Our project will whow a simple pipeline unabling to allow argo CD following gitops principles to track any changes into our source code repository and deploy them into our kubernetes cluster

Preresuisites:
- a source code repository containing the application configuration ( we will use a repository into github)
- a kubernetes cluster ( since we are into a test workflow , we will make do with a microk8s cluster)

For this task the idea is to follow how argo cd track the changes into our source code repo in order to deploy the desired state into the actual state into the cluester
We want to showcwase using a small chnage of images of our deployments container images . we will make a simple pdeployment with a hello-world image that will be substitute by a ngninx image and see how argocd implement the new changes 
appearing into the cluster 

Requirements¶
Installed kubectl command-line tool.
Have a kubeconfig file (default location is ~/.kube/config).
CoreDNS. Can be enabled for microk8s by `microk8s enable dns && microk8s stop && microk8s start`

there will be steps

1. we create a repo with a folder containing the apllication configuration yaml file

2.Install Argo CD

`kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable`
These steps will install some necessary objects for argo cd to run correctly

3. another file containing the argo cd application into the github repository
   
5. we deploy the argo cd deployment to make 
