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
     You can take the app config files into the dev rfolder inside our repository. the initial container image is hello-world that e will change into nginx
   
2.Install Argo CD

`kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable`
[![Screenshot-from-2023-10-07-12-57-53.png](https://i.postimg.cc/yY4kV375/Screenshot-from-2023-10-07-12-57-53.png)](https://postimg.cc/6Tc9c32L)
These steps will install some necessary objects for argo cd to run correctly

3. another file containing the argo cd application into the github repository
   see the argo-application.yaml 
   
5. we then allow the process to go ahead using:
   `kubectl apply -f application.yaml` into the folder

6. we can reach to the argocd UI this way :
   `kubectl port-forward -n argocd svc/argocd-server 8080:443`
   [![Screenshot-from-2023-10-07-14-07-13.png](https://i.postimg.cc/x11rBmsM/Screenshot-from-2023-10-07-14-07-13.png)](https://postimg.cc/TpFHDKv3)
   



