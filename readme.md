# 🚀 Creating an Amazon EKS Cluster Using `eksctl`

To create an Amazon EKS cluster using a configuration file named **eks.yaml**:

```bash
eksctl create cluster --config-file=eks.yaml
📘 EKS Cluster & Node Group Configuration (eksctl)
This section explains the Amazon EKS cluster and managed node group created using the following eksctl configuration file.

📄 eksctl ClusterConfig
yaml
Copy code
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: sampleapp
  region: us-east-1

managedNodeGroups:

  - name: roboshop-dev
    instanceTypes: ["m5.large","t3.small", "t3.medium","c5.large"]
    desiredCapacity: 2
    spot: true
🚀 Resources Created
EKS Cluster: eksctl-sampleapp-cluster

Managed Node Group: eksctl-sampleapp-nodegroup-roboshop-dev

🔍 Configuration Breakdown
### Cluster Metadata
Field	Description
name	Name of the EKS cluster. (sampleapp)
region	AWS region (us-east-1, N. Virginia).

👷 Managed Node Group
Node Group Name
roboshop-dev

Creates a managed node group associated with the cluster.

Instance Types
yaml
Copy code
instanceTypes: ["m5.large","t3.small","t3.medium","c5.large"]
Multiple instance types provide flexibility and improve Spot availability.

Benefits:

Better chances of getting Spot capacity

Lower overall compute cost

Automatic instance selection by AWS

Desired Capacity
yaml
Copy code
desiredCapacity: 2
Initial number of worker nodes in the node group.
(Default is 3; this config sets it to 2.)

Spot Instances
yaml
Copy code
spot: true
Enables EC2 Spot Instances for cost optimization.

Pros:

50–70% cheaper than On-Demand

Great for dev/test workloads

Cons:

Nodes can be interrupted (2-minute warning)
```
