# CMS-kata-new
My repo for exercise


Question:  

You will need to:
    1. Create a new git public GitHub (or similar services) repository and work there.
    2. Automate the creation of the infrastructure and the setup of the Joomla application.

Solution:


Have to clone https://github.com/kubernetes/kubernetes and build kubernetes framework on Linux environment and hence, have to use “kubectl” as it is the command with which we can manage the infrastructure.


1. create the cluster:

$ minikube start 

>create the infrastructure with one master node. 

$ kubectl get nodes

>see the nodes avaiable.

2. deployment of the application:

$ kubectl create -f joomla.yaml

>create the deployment

$ kubectl get deplyments

>get the deployments

3. explore the deployments:

$ kubectl get pods

>verify if the application deployed is running fine.

$ kubectl describe pods

>see the details of the container running in the pod.

4. expose as service:

$ kubectl expose deployments/joomla type=”NodePort” --port=8080

>expose as service the application as pods are mortal.

$ kubectl get services

$ kubectl describe services/joomla 

>see if services are running

5. scaling the application:

$ kubectl get deployments
$ kubectl scale deployments/joomla --replicas=4

>scale the application upto 4 replicas

$ kubectl get deployments
$ kubectl get pods

>verify running of the aplication and replicas.

6. automate the running of the deployed application:

$ kubectl autoscale deployment joomla –cpu-percent=50 –min=1 --max=10

>the horizontal pod autoscalar will maintain between 1 to 10 replicas of the application deployed “joomla application”, whenever the cpu utilization across all the pods is more than 50%. 

$ kubectl get hpa

>current status of the autoscalar. Whenever the load increase on the joomla application, the result will keep changing and hence we can control the infrastructure and deploymentof the application automatically.







