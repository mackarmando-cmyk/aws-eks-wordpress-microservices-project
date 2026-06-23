Test Results

Test 1: Application Deployment

**Objective**:
Verify Helm successfully deploys the application.

**Command**:

```bash
helm install my-microservice .

**Expected Result:**
Deployment created successfully.

**Actual Result**:
Deployment created successfully.

**Status**:
PASS

**Evidence**:
Screenshot 14


Test 2: Load Balancer Accessibility**

Objective:
Verify application is accessible through AWS Load Balancer.

**Command**:

```bash
kubectl get svc

**Expected Result**:
External LoadBalancer URL assigned.

**Actual Result**:
AWS ELB URL assigned successfully.

**Status**:
PASS

**Evidence**:
Screenshot 17
Screenshot 18


**Test 3: HPA Creation**

**Objective**:
Verify Horizontal Pod Autoscaler creation.

**Command**:

kubectl apply -f hpa.yaml

**Expected Result**:
HPA resource created.

**Actual Result**:
HPA resource created successfully.

**Status**:
PASS

**Evidence**:
Screenshot 22


**Test 4: Siege Load Test**

**Objective**:
Generate load against application.

**Command**:

kubectl run siege \
--image=jacobvhs/siege \
--restart=Never \
-- /bin/sh -c "siege -c 500 -t 15m http://<ELB_URL>"

**Expected Result**:
Traffic generated to application.

**Actual Result**:
Traffic generated successfully.

**Status**:
PASS

**Evidence**:
Screenshot 27
Screenshot 28


**Test 5: HPA Monitoring**

**Objective**:
Verify HPA metrics are visible.

**Command**:

kubectl get hpa -w

**Expected Result**:
HPA reports CPU utilization.

**Actual Result**:
HPA reported CPU metrics.

**Status**:
PASS

**Evidence**:
Screenshot 29

