# Exam Basics
## Basics
* Why K8's and what does it solve?
* YAML basics
* JSON*\

## Commands
* `kubectl`
	* what it is
* K8's API resources
	* `kubectl api-resources`
* Imperative commands
	* Just remember that most of the time you will have to create, get, delete, run & expose api-resources. Here you go now and type kubectl followed by create, get, delete, run or expose followed by resources you get from kubectl api-resources followed by --help option. You will get a ton of examples. To summarize 
		* `kubectl create deploy --help | grep -i example -A20` is your magic command (in exam) if you don’t remember the parameters of deploy command (thank me later :)) 
		* `kubectl explain <kubernetes-object> --recursive | less -S` is my favourite command to understand the spec.
		* `kubectl <command> --dry-run=client -o yaml` gives the command in yaml that you can edit later if needed. Use it in the exam whenever needed. 
			* Note that daemonset, replicaset and deployment specs are almost identical. Use kubectl deploy create command to create yaml and update it to create daemonset or replicaset. 
		* `kubectl get all --show-labels` is the best way to see all resources in a namespace. Labels are very important in k8s. 
		* `kubectl get <kubernetes-objects> --all-namespaces` helps you quickly understand the cluster you are dealing with
			*  Save your keystrokes. Use [Alias](http://faculty.salina.k-state.edu/tim/unix_sg/bash/alias.html) commands. For example once you run this command alias k=kubectl then you can just type k for kubectl
    

## Cluster:
* Easy to create a cluster on Google Cloud Kubernetes Engine to practise. Don't waste your time in provisioning a cluster of your own on your laptop. If you don’t have an account, create a free one at [https://cloud.google.com/free](https://cloud.google.com/free).  I created a GKE cluster initially and then eventually built my own cluster using Google Cloud VMs. (pro tip: Shutdown cluster when not in use + create 2 core VMs if you are building a cluster. Single core VMs don’t run k8s)
* Training is essential. Try coursera, linux academy, kodekloud and so on. Anything that helps you cover all aspects of k8s curriculum. Pro-tip: Don’t leave any section in curriculum. All sections are covered in the exam. 

## Documentation:
* In the exam candidate can open one additional tab in order to access assets at: [https://kubernetes.io/docs/](https://kubernetes.io/docs/) , [https://github.com/kubernetes/](https://github.com/kubernetes/) , [https://kubernetes.io/blog/](https://kubernetes.io/blog/) and their subdomains. This includes all available language translations of these pages (e.g. [https://kubernetes.io/zh/docs/](https://kubernetes.io/zh/docs/) )
* No other tabs may be opened and no other sites may be navigated to   (including [https://discuss.kubernetes.io/](https://discuss.kubernetes.io/) ). 
* So focus on k8s documentation. I clicked on almost every page of k8s documentation beforehand to understand what is there in it. You don’t need to do it, but you should understand how it's organized. 
* Pro-tip: What I observed is both Google Cloud and Microsoft Azure documentation pages are similar to k8s documentation in their layout and navigation. So its an advantage if you know k8s documentation in detail you will understand most of the cloud provider's documentation layouts. 
* Don’t rely on k8s documentation too much. You won’t have time to read in the exam. Aim to understand & remember which page has the details you need. That should be good enough for the exam.**
	
## Security:
* Understand certificates and basics of openssl
* This was the most confusing concept in k8s when I started my preparation. Allocate more time if you are very new to TLS and other security concepts.
* Pro-tip: RBAC (roles and bindings) is similar to Google Cloud RBAC. So if you know one there is a high chance that you will know the second one easily. 
* This [blog](https://www.cncf.io/blog/2018/08/01/demystifying-rbac-in-kubernetes/) might help you. 
    
## Network:

-   Deploy weave-net when asked for a network plugin. 
    

-   Reason - You can find installation command in documentation which you can open and refer in exam for at [https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/#set-up-the-first-control-plane-node](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/#set-up-the-first-control-plane-node) 
    

-   For the rest of other networking deployments you need to remember them. 
    
-   Debugging issues can be related to network not deployed. So watch out. 
    
-   Understand why CNI. 
    

  

## Linux:
* You cannot get away without knowing linux. Some (not all) of the commands and tools that you need to know in and out are:
	* grep
	*  journalctl
	*  ps aux
	*  vi
	*  docker
	*  systemd 
	*  service 
	*   ip link
	*   netstat
	*   tmux
	*   openssl
	*    nslookup etc.
*    Remember k8s deployment paths. They are very useful in debugging scenarios. 
    
## Kubernetes the hard way:
* Understand every step in Kubernetes the hard way [https://github.com/kelseyhightower/kubernetes-the-hard-way](https://github.com/kelseyhightower/kubernetes-the-hard-way)*
	* Pro-tip: Don’t just execute commands. Learn the process. Commands can be found in the documentation pages. 
		* Understand different k8s deployment components & their roles in running clusters. 
		*  HA configuration might not be relevant for the exam but good to know.
		*   There are so many different courses and books for this. 
    

## Practice:

-   There is no shortcut for cka. You need to practise the commands. 
    
-   Challenge yourself with a lot of scenarios and practise commands as much as possible.
    
-   If you know the command and what to do as soon as you see the question then you will definitely pass the exam. Remember that you will not have time to read documentation in the exam. You can just refer to it. 
    
-   There are some lab practices like [this](https://github.com/stretchcloud/cka-lab-practice). I did not use them but they might be useful. 
    

During the exam: 
-   You need to answer 24 questions in 3 hours. So you have approximately 7 minutes for each question & some of them might just take 2 mins. Plan properly. 
-   Read questions very carefully & do exactly what they asked for. Note that scoring is automatic. If the format of output and even name of POD created is different than they asked for then its a wrong answer. 
    
-   Always verify the answer once you save the answer. This will be the biggest mistake if you don’t do it.
    
-   Debugging questions are most time consuming. Don’t waste time on them. Understand the weightage of those questions. I lost one question in the debugging section which has a 4% weightage (yes, I know where I lost my score :)). 
    
-   I don’t want to retype the candidate hand book. But you can find it [here](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook). Read carefully.**

---
## CKA Material
* ![[Screen Shot 2022-04-25 at 12.28.33 PM.png]]

---
# Study Materials
[Kubernetes Certification Study Group Playlist](https://www.youtube.com/playlist?list=PLVTrNddhdNd1rCA8kYyMqypyHYutLlzLY)
## Creating pods and deployments
* Quick review of core concepts; study ways to create pods and deployments in exams; The topic includes creating single and multi-container pods and deployments, scaling deployments, updating existing resources and basic testing and troubleshooting
	* [`Kubeadm`, Pods & Deployments by Carlos Ortiz](https://www.youtube.com/watch?v=JUuXFPUMzgU&list=PLVTrNddhdNd1rCA8kYyMqypyHYutLlzLY&index=3)

## Storage volumes and Data Persistence
* Review storage classes, CSI and legacy drivers, volume claims and volumes; Understand volume types, access modes and reclaim policies; The topic includes the use of known persistent volume types used in exams

## Secrets and configurations
* Review ways to inject data into pods at start time and after; The topic includes defining environment variables using different sources (pod's properties, config maps, secrets) and mounting config maps, secrets, local drivers and pod's data as volumes

## Observability and troubleshooting
* In depth session on troubleshooting (mainly for CKA exam) that includes troubleshooting running workloads (in pods); troubleshooting other resources such as jobs or services) and clusters

## Cluster provisioning
* (May require [K8S the hardway](https://github.com/kelseyhightower/kubernetes-the-hard-way) as prerequisite) [CKA exam] Provision cluster; Add node to a cluster; May partially overlap with troubleshooting topic

## Controlling workloads
* Includes deployment scaling and upgrading (as well as downgrading); jobs and cron jobs creation, execution and result capturing; Work with health probing and contrlling startup and end of the workloads;

### Controlling workloads (2)
* Node affinity and pod affinity; node taints and other fun with labels and annotations
* Networking
* Review types of services (TODO: verify if need any focus for LB type for exam); Troubleshoot networking; Network policies

## Security
* Understand service accounts and how they are used in RBAC; Review all properties in the SecurityContext in pod and container levels


---
