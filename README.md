# Kubernetes - Deployment Strategies



**Step-01: What are Deployment strategies?**
- Kubernetes offers several deployment strategies to handle a broad range of application development and deployment needs. 
- Once you define the desired state of the application, the deployment controller goes to work. It can make changes at a controlled rate to optimize the deployment. 

**Recreate:**
- The recreate strategy terminates pods that are currently running and ‘recreates’ them with the new version. 
- This approach is commonly used in a development environment where user activity isn’t an issue.
- Because the recreate deployment entirely refreshes the pods and the state of the application, you can expect downtime due 
to the shutdown of the old deployment and the initiation of new deployment instances.

**Rolling Update**
- The rolling update deployment provides an orderly, ramped migration from one version of an application to a newer version. 
- A new ReplicaSet with the new version is launched, and replicas of the old version are terminated systematically as replicas of the new version launch. Eventually, all pods from the old version are replaced by the new version. 
- The rolling update deployment is beneficial because it provides an organized transition between versions. However, it can take time to complete.  

**Blue/Green**
- The Blue/Green strategy offers a rapid transition from the old to new version once the new version is tested in production. 
- Here the new ‘green’ version is deployed along with the existing ‘blue’ version. Once there is enough confidence that the ‘green’ version is working as designed,
the version label is replaced in the selector field of the Kubernetes Service object that performs load balancing. 
- This action immediately switches traffic to the new version.
- The Kubernetes blue/green deployment option provides a rapid rollout that avoids versioning issues. However, this strategy doubles the resource utilization since both versions run until cutover.

**Canary**
- In a canary deployment, a small group of users is routed to the new version of an application, which runs on a smaller subset of pods. 
- The purpose of this approach is to test functionality in a production environment. Once satisfied that testing is error-free, replicas of the new version are scaled up, and the old version is replaced in an orderly manner.
- Canary deployments are beneficial when you want to test new functionality on a smaller group of users. Since you can easily roll back canary deployments, this strategy helps gauge how new code will impact the overall system operation without significant risk.


**Step-02: How to Create a Deployment**
- Create Deployment and service using the manifest files provided.
- Verify Deployment, ReplicaSet, Service & Pods
```
# Create Deployment
kubectl apply -f <file-name.yaml>

# Verify Deployment
kubectl get deployments
kubectl get deploy 

# Verify Service
kubectl get service
kubectl get svc

# Describe Deployment
kubectl describe deployment <deployment-name>
kubectl describe deployment my-first-deployment

# Verify ReplicaSet
kubectl get rs

# Verify Pod
kubectl get po
```
