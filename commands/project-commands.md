AWS EKS WordPress Deployment Command Reference
**1. Verify Tools**
aws --version
kubectl version --client
eksctl version
helm version

**2. Verify AWS Authentication**
aws sts get-caller-identity

**3. Create EKS Cluster**
eksctl create cluster \
--name enterprise-cluster \
--region us-east-1 \
--nodegroup-name standard-workers \
--node-type t3.medium \
--nodes 3

**4. Verify Worker Nodes**
kubectl get nodes

**5. Create Helm Chart**
helm create my-microservice

**6. Navigate Into Chart**
cd my-microservice

**7. Modify values.yaml**
Update:

service:
  type: LoadBalancer
  port: 80

**8. Install Helm Release**
helm install my-microservice .

**9. Verify Helm Deployment**
helm list
helm status my-microservice

**10. Verify Kubernetes Resources**
kubectl get pods
kubectl get svc

**11. Access Application**
Retrieve Load Balancer URL:

kubectl get svc

Open:

http://<LOADBALANCER-URL>

**12. Create HPA Manifest**

Create:

touch hpa.yaml

Contents:

apiVersion: autoscaling/v1
kind: HorizontalPodAutoscaler

metadata:
  name: wordpress-hpa

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: my-microservice

  minReplicas: 1
  maxReplicas: 5

  targetCPUUtilizationPercentage: 50

**13. Apply HPA**
kubectl apply -f hpa.yaml

**14. Verify HPA**
kubectl get hpa

**15. Monitor HPA Live**
kubectl get hpa -w

**16. Verify Metrics Server**
kubectl top pods

(Optional)

kubectl top nodes

**17. Create Load Test Pod (Initial Attempt)**
kubectl run siege \
--image=jtrarcher/siege \
--restart=Never \
-- /bin/sh -c "siege -c 500 -t 15m http://<LOADBALANCER-URL>"

**18. Troubleshoot ImagePullBackOff**

Verify:

kubectl get pods

Observe:

ImagePullBackOff

**19. Delete Failed Siege Pod**
kubectl delete pod siege

**20. Relaunch Siege With Correct Image**
kubectl run siege \
--image=jstarcher/siege \
--restart=Never \
-- /bin/sh -c "siege -c 500 -t 15m http://<LOADBALANCER-URL>"

**21. Verify Siege Running**
kubectl get pods

Expected:

my-microservice    Running
siege              Running

**22. Monitor HPA During Load Test**
kubectl get hpa -w

Expected:

cpu: 1%/50%
cpu: 2%/50%
cpu: 3%/50%

or higher.

**23. Verify Deployment Status**
helm status my-microservice

**24. Verify Services**
kubectl get svc

**25. Verify Deployments**
kubectl get deployments

**26. Verify Pods**
kubectl get pods

**27. Verify Nodes**
kubectl get nodes

**Cleanup Commands (Important)**

If you want to destroy everything later:

Delete Helm Release
helm uninstall my-microservice
Delete HPA
kubectl delete -f hpa.yaml
Delete EKS Cluster
eksctl delete cluster \
--name enterprise-cluster \
--region us-east-1
