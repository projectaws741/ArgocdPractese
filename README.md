For Gihub actions add the secrtes in gihubaction secrets.

There will be issue for authentication. We have to manully add the user related info in eks cluster.

apiVersion: v1
data:
  mapRoles: |
    - groups:
      - system:bootstrappers
      - system:nodes
      rolearn: arn:aws:iam::<Account_ID>:role/eksctl-my-eks-cluster-nodegroup-st-NodeInstanceRole-IaBGwqTIkM2m
      username: system:node:{{EC2PrivateDNSName}}
  mapUsers: |
    - userarn: arn:aws:iam::<Account_ID>:user/app
      username: app
      groups:
        - system:masters
kind: ConfigMap
metadata:
  creationTimestamp: "2025-04-17T15:14:57Z"
  name: aws-auth
  namespace: kube-system
  resourceVersion: "1293"
  uid: 4b218873-a0a6-4862-8884-af2bbebd355d

  Here we have to add mapUsers if we have using users accesskey and secret accesskey.
