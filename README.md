# GENAI_AWS_CSPM_Security_Threat_Agent
Langgraph Agent for CSPM usecase

# PROBLEM: 

Its  difficult  to understand  the  relationship  between  Cloud  IAM  privilege  role  escalation  security attacks in a  Multi-Cloud Context  
(CSPM  usecase).  

# SOLUTION:  

There is a need to have GENAI  based  interactive graphical interface to understand access relationships between AWS identities and AWS resources.
It  could be  “Security Threat  Signature Text data  to Visual Graph generation based with  GENAI  LLM approaches”

As on  today AWS IAM offers a variety of  customizability, but it can be daunting to understand IAM access relationships. Basic questions like “Which IAM users can access sensitive customer PII data?” can be challenging to answer for security and devops teams.

Improperly configured AWS IAM roles, users, and policies provide a concrete way for attackers to laterally move through the cloud environment. So, from a security perspective, it is critical to have visibility into IAM relationships.

In this project, we review 2 potential use cases of Access Explorer: protecting sensitive S3 data and curbing over-permissive roles attached to publicly exposed compute.

Protecting Sensitive S3  Bucket’s Data:
========================================
Lateral movements using overly-permissive  access policies are common in AWS  CSPM  based  cloud attacks - just consider the infamous crypto Onus attacks.
AWS customers need better answers to the question: “Who can access my most sensitive data?” 

Teams may want to know who can read objects from a particular sensitive S3 bucket.  	We need  to  create a  visualization  about which IAM roles and users can run a s3:GetObject action by incorporating details like S3 bucket policies, IAM policies attached to roles, etc.. 

For example, consider the visual about the s3 bucket: s3stack-bucketencryptedbypolicy167af7b6-13wo0103igbyj315957380126

![64777b34ec1cde2bf868935c_b0aabcf9](https://github.com/user-attachments/assets/475b3412-ae2f-4281-aa70-f2eae1205bc3)

We learn that the role: cdk-hnb659fds-deploy-role-315957380126-us-west-2 can do a privilege escalation to an admin role using iam:PassRole & cloudformation:UpdateStack. 

![64777b410d5e1b4a14735fd4_0e53d070](https://github.com/user-attachments/assets/f81fe794-37c4-4a73-a652-7e8448da59d7)

It can also read the S3 bucket directly because of the inline policy attached to it (displayed below).

![64777b4e86afc4da3dd76364_485b5356](https://github.com/user-attachments/assets/fb9e3d6e-0722-4c6c-a6ea-ca60e6823323)

The edges explain how IAM users and roles can laterally move and perform the s3:GetObject action. With such context, teams can get a better understanding of the identity visuals in their cloud environments.

Over-permissive IAM Roles Attached to Compute

In the infamous Capital One Breach, attackers gained access to an EC2 through a misconfigured firewall and an SSRF vulnerability. Once inside, the attacker was able to discover and exfiltrate sensitive data from an S3 bucket. The role attached to the EC2’s was over-permissive and gave the attacker access to substantial resources. ZeusCloud provides a mechanism to show how an IAM role attached to a compute instance can move laterally to gain greater access within a cloud environment. 

The diagram shows how an IAM Role attached to an EC2 can laterally privilege escalate permissions.

![64777b63a4ea991a0db33e42_95968704](https://github.com/user-attachments/assets/55a7e49e-60fe-40b3-af4d-7526b9dbf7ca)

![64777b632f9b74ee68be0d44_fe797ba0](https://github.com/user-attachments/assets/dfe19479-1475-4038-b87b-1e13a47f6413)

![64777b63aa5c8de6b2f05b8b_8e2b54ca](https://github.com/user-attachments/assets/e1851536-994f-46fe-8e0c-c039794255e0)











‍
