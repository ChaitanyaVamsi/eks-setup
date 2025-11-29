# 🚀 Creating an Amazon EKS Cluster Using `eksctl`

To create an Amazon EKS cluster using a configuration file named **eks.yaml**, run:

```bash
eksctl create cluster --config-file=eks.yaml

📘 EKS Cluster & Node Group Configuration (eksctl)
Below is the eksctl configuration file used to create the EKS cluster and managed node group.

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
    instanceTypes: ["m5.large", "t3.small", "t3.medium", "c5.large"]
    desiredCapacity: 2
    spot: true
🚀 Resources Created
Resource Type	Name
EKS Cluster	eksctl-sampleapp-cluster
Managed Node Group	eksctl-sampleapp-nodegroup-roboshop-dev

🔍 Configuration Breakdown
🏷 Cluster Metadata
Field	Description
name	Name of the EKS cluster (sampleapp)
region	AWS region (us-east-1)

👷 Managed Node Group Details
Node Group Name
roboshop-dev
Creates a managed node group attached to the EKS cluster.

🖥 Instance Types
yaml
Copy code
instanceTypes: ["m5.large", "t3.small", "t3.medium", "c5.large"]
Using multiple instance types provides:

Better Spot availability

Lower compute cost

Automatic optimal instance selection by AWS

📦 Desired Capacity
yaml
Copy code
desiredCapacity: 2
Sets initial worker node count to 2 (default is 3).

💸 Spot Instances
yaml
Copy code
spot: true
Enables EC2 Spot Instances for cost optimization.

Pros:

50–70% cheaper than On-Demand

Great for dev/test environments

Cons:

Instances may be interrupted (2-minute notice)

🏗 Summary
This configuration creates:

An EKS cluster named sampleapp

A managed node group named roboshop-dev

Uses 2 Spot EC2 nodes

Flexible instance types for cost efficiency and high availability

Ideal for development and non-production workloads where cost savings matter.
```
