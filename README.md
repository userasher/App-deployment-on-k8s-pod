# App-deployment-on-k8s-pod
installation of minikube, kubectl and docker so that we can easily manage the app we are deploying on the k8s pod

Most important ==> all the commands used in tutorial is given (just type kubectl cheatsheet cheatsheet)

for installing docker ==> use abhishek veermala's Docker zero to hero playlist(https://github.com/iam-veeramalla/Docker-Zero-to-Hero)

for installing kubectl,just be sure check your architecture before you use the command 
=====> go to geeks for geeks kubectl installation tutorial: https://www.geeksforgeeks.org/install-and-set-up-kubectl-on-linux/

for installing minikube you just need one command:
some important points to be remeber before:
![image](https://github.com/userasher/App-deployment-on-k8s-pod/assets/109350583/84aacd74-0f86-4b35-8996-4fab7db9a10a)


1) In your linux terminal type lscpu to know the architecture of your cpu
2) Now match the config. as shown in command to get desired command for installing minikube



Now just type minikube, Docker and kubectl and if output is command not found repeat the above process foe the specific command

Very important point before moving forward:
1) after istallatiion of docker be sure to include your root user in the docker group else minikube can't access docker daemon.
2) after typing this command ![image](https://github.com/userasher/App-deployment-on-k8s-pod/assets/109350583/4bbd61ba-3de1-4b9a-be22-2b87a5f22e1f). Be sure to restart the your docker by using command "sudo systemctl restart docker"


Now we have successfully configured all 3 which is required and we can move ahead with cluster, pod creation.

steps to follow and commands to execute:
1)command : minikube start
(this will automatically create a k8s cluster)

2) command: kubectl get nodes
(will list that k8s node is created which is the control plane node)

3)Now we need a pod inside our node so that our appl. can run inside our pod

4)In k8s we describe the specifications of pod into an yaml file (for more info. just go to https://kubernetes.io/docs/concepts/workloads/pods/)
5) now create a file using command : "vi pod.yml" and paste and don't forget to save ![image](https://github.com/userasher/App-deployment-on-k8s-pod/assets/109350583/0922e27a-d062-4c7e-ad99-d782d7836685)

6) you can find it https://kubernetes.io/docs/concepts/workloads/pods/
   
7)After this execute the command: kubectl create -f pod.yml (this will create a pod accordign to the specifications given in the pod.yml file.....be sure to change the port in case connection is refused)

8)Now to check if pod is running run command: "kubectl get pods" or "kubectl get pods -o wide"(this command will give you the ip address of the pod to ssh into the pod)

9)simply ssh into the pod using command: minikube ssh

10) Now to get the output of the application running on the type the command: curl <ipaddress>(that ipaddress which you got after typing "kubectl get pods -o wide" command)

11) That's it our application is running on the k8s pod.






   

