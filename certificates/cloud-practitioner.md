## AWS - Cloud Practitioner

A summary of what you need to know for the exam can be found [here](https://codingshell.com/aws-cloud-practitioner)

#### Cloud 101

<details>
<summary>What types of Cloud Computing services are there?</summary><br><b>

IAAS
PAAS
SAAS
</b></details>

<details>
<summary>Explain each of the following and give an example:

  * IAAS
  * PAAS
  * SAAS</summary><br><b>
</b></details>

<details>
<summary>What types of clouds (or cloud deployments) are there?</summary><br><b>

  * Public
  * Hybrid
  * Private
</b></details>

<details>
<summary>Explain each of the following Cloud Computing Deployments:

  * Public
  * Hybrid
  * Private</summary><br><b>
</b></details>

#### AWS Global Infrastructure

<details>
<summary>Explain the following

  * Availability zone
  * Region
  * Edge location</summary><br><b>
AWS regions are data centers hosted across different geographical locations worldwide, each region is completely independent of one another.<br>

Within each region, there are multiple isolated locations known as Availability Zones. Multiple availability zones ensure high availability in case one of them goes down.<br>

Edge locations are basically content delivery network which caches data and insures lower latency and faster delivery to the users in any location. They are located in major cities in the world.
</b></details>

#### AWS Networking

<details>
<summary>What is VPC?</summary><br><b>

"A logically isolated section of the AWS cloud where you can launch AWS resources in a virtual network that you define"
Read more about it [here](https://aws.amazon.com/vpc).
</b></details>

<details>
<summary>True or False? VPC spans multiple regions</summary><br><b>

False
</b></details>

<details>
<summary>True or False? Subnets belong to the same VPC, can be in different availability zones</summary><br><b>

True. Just to clarify, a subnet must reside entirely in one AZ.
</b></details>

<details>
<summary>What is an Internet Gateway?</summary><br><b>

"component that allows communication between instances in your VPC and the internet" (AWS docs).
Read more about it [here](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html)
</b></details>

<details>
<summary>Multiple Internet Gateways can be attached to one VPC</summary><br><b>

False. Only one internet gateway can be attached to a single VPC.
</b></details>

<details>
<summary>True or False? Route Tables used to allow or deny traffic from the internet to AWS instances</summary><br><b>

False.
</b></details>

<details>
<summary>Explain Security Groups and Network ACLs</summary><br><b>

* NACL - security layer on the subnet level.
* Security Group - security layer on the instance level.

Read more about it [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) and [here](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)
</b></details>

<details>
<summary>What is AWS Direct Connect?</summary><br><b>

Allows you to connect your corporate network to AWS network.
</b></details>

#### AWS Compute

<details>
<summary>What is EC2?</summary><br><b>

"a web service that provides secure, resizable compute capacity in the cloud".
Read more [here](https://aws.amazon.com/ec2)
</b></details>

<details>
<summary>What is AMI?</summary><br><b>

Amazon Machine Images is "An Amazon Machine Image (AMI) provides the information required to launch an instance".
Read more [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)
</b></details>

<details>
<summary>What are the different source for AMIs?</summary><br><b>

* Personal AMIs - AMIs you create
* AWS Marketplace for AMIs - Paid AMIs usually with bundled with licensed software
* Community AMIs - Free
</b></details>

<details>
<summary>What is instance type?</summary><br><b>

"the instance type that you specify determines the hardware of the host computer used for your instance"
Read more about instance types [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html)
</b></details>

<details>
<summary>What is EBS?</summary><br><b>

"provides block level storage volumes for use with EC2 instances. EBS volumes behave like raw, unformatted block devices."
More on EBS [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)
</b></details>

<details>
<summary>What EC2 pricing models are there?</summary><br><b>

On Demand - pay a fixed rate by the hour/second with no commitment. You can provision and terminate it at any given time.
Reserved - you get capacity reservation, basically purchase an instance for a fixed time of period. The longer, the cheaper.
Spot - Enables you to bid whatever price you want for instances or pay the spot price.
Dedicated Hosts - physical EC2 server dedicated for your use.
</b></details>

<details>
<summary>What are Security Groups?</summary><br><b>

"A security group acts as a virtual firewall that controls the traffic for one or more instances"
More on this subject [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)
</b></details>

#### AWS Storage
 
<details>
<summary>Explain what is AWS S3?</summary><br><b>

S3 stands for 3 S, Simple Storage Service.
S3 is a object storage service which is fast, scalable and durable. S3 enables customers to upload, download or store any file or object that is up to 5 TB in size.

More on S3 [here](https://aws.amazon.com/s3) 
</b></details>

<details>
<summary>What is a bucket?</summary><br><b>

An S3 bucket is a resource which is similar to folders in a file system and allows storing objects, which consist of data.
</b></details>

<details>
<summary>True or False? A bucket name must be globally unique</summary><br><b>

True
</b></details>

<details>
<summary>Explain folders and objects in regards to buckets</summary><br><b>

* Folder - any sub folder in an s3 bucket
* Object - The files which are stored in a bucket
</b></details>

<details>
<summary>Explain the following:

  * Object Lifecycles
  * Object Sharing
  * Object Versioning</summary><br><b>

  * Object Lifecycles - Transfer objects between storage classes based on defined rules of time periods
  * Object Sharing - Share objects via a URL link
  * Object Versioning - Manage multiple versions of an object
</b></details>

<details>
<summary>Explain Object Durability and Object Availability</summary><br><b>

Object Durability: The percent over a one-year time period that a file will not be lost
Object Availability: The percent over a one-year time period that a file will be accessible
</b></details>

<details>
<summary>What is a storage class? What storage classes are there?</summary><br><b>

Each object has a storage class assigned to, affecting its availability and durability. This also has effect on costs.
Storage classes offered today:
  * Standard:
    * Used for general, all-purpose storage (mostly storage that needs to be accessed frequently)
    * The most expensive storage class 
    * 11x9% durability
    * 2x9% availability
    * Default storage class

  * Standard-IA (Infrequent Access)
    * Long lived, infrequently accessed data but must be available the moment it's being accessed
    * 11x9% durability
    * 99.90% availability

  * One Zone-IA (Infrequent Access):
    * Long-lived, infrequently accessed, non-critical data
    * Less expensive than Standard and Standard-IA storage classes
    * 2x9% durability
    * 99.50% availability
    
  * Intelligent-Tiering:
    * Long-lived data with changing or unknown access patterns. Basically, In this class the data automatically moves to the class most suitable for you based on usage patterns
    * Price depends on the used class
    * 11x9% durability
    * 99.90% availability

  * Glacier: Archive data with retrieval time ranging from minutes to hours
  * Glacier Deep Archive: Archive data that rarely, if ever, needs to be accessed with retrieval times in hours
  * Both Glacier and Glacier Deep Archive are:
    * The most cheap storage classes
    * have 9x9% durability 

More on storage classes [here](https://aws.amazon.com/s3/storage-classes)

</b></details>

<details>
<summary>Explain what is Storage Gateway</summary><br><b>

"AWS Storage Gateway is a hybrid cloud storage service that gives you on-premises access to virtually unlimited cloud storage".
More on Storage Gateway [here](https://aws.amazon.com/storagegateway)
</b></details>

<details>
<summary>Explain the following Storage Gateway deployments types

  * File Gateway
  * Volume Gateway
  * Tape Gateway</summary><br><b>

Explained in detail [here](https://aws.amazon.com/storagegateway/faqs)
</b></details>

<details>
<summary>What is the difference between stored volumes and cached volumes?</summary><br><b>

Stored Volumes - Data is located at customer's data center and periodically backed up to AWS
Cached Volumes - Data is stored in AWS cloud and cached at customer's data center for quick access
</b></details>

#### AWS IAM

<details>
<summary>What is IAM? What are some of its features?</summary><br><b>

Full explanation is [here](https://aws.amazon.com/iam)
In short: it's used for managing users, groups, access policies & roles
</b></details>

<details>
<summary>True or False? IAM configuration is defined globally and not per region</summary><br><b>

True
</b></details>

<details>
<summary>Given an example of IAM best practices?</summary><br><b>

* Set up MFA
* Delete root account access keys
* Create IAM users instead of using root for daily management
</b></details>

<details>
<summary>What are Roles?</summary><br><b>

A way for allowing a service of AWS to use another service of AWS. You assign roles to AWS resources.
For example, you can make use of a role which allows EC2 service to acesses s3 buckets (read and write).
</b></details>

<details>
<summary>What are Policies?</summary><br><b>

Policies documents used to give permissions as to what a user, group or role are able to do. Their format is JSON.
</b></details>

<details>
<summary>A user is unable to access an s3 bucket. What might be the problem?</summary><br><b>

There can be several reasons for that. One of them is lack of policy. To solve that, the admin has to attach the user with a policy what allows him to access the s3 bucket.
</b></details>

<details>
<summary>What should you use to:

  * Grant access between two services/resources?
  * Grant user access to resources/services?</summary><br><b>

  * Role
  * Policy
</b></details>

<details>
<summary>What permissions does a new user have?</summary><br><b>

Only a login access.
</b></details>

##### AWS ELB

<details>
<summary>What is ELB (Elastic Load Balancing)?</summary><br><b>

AWS definition: "Elastic Load Balancing automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions."

More on ELB [here](https://aws.amazon.com/elasticloadbalancing)
</b></details>

<details>
<summary>What is auto scaling?</summary><br><b>

AWS definition: "AWS Auto Scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost"

Read more about auto scaling [here](https://aws.amazon.com/autoscaling)
</b></details>

<details>
<summary>True or False? Auto Scaling is about adding resources (such as instances) and not about removing resource</summary><br><b>

False. Auto scaling adjusts capacity and this can mean removing some resources based on usage and performances.
</b></details>

<details>
<summary>What types of load balancers are supported in EC2 and what are they used for?</summary><br><b>

  * Application LB - layer 7 traffic
  * Network LB - ultra-high performances or static IP address
  * Classic LB - low costs, good for test or dev environments
</b></details>

#### AWS DNS

<details>
<summary>What is Route 53?</summary><br><b>

"Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service"
Some of Route 53 features:
  * Register domain
  * DNS service - domain name translations
  * Health checks - verify your app is available

More on Route 53 [here](https://aws.amazon.com/route53)
</b></details>

#### AWS CloudFront

<details>
<summary>Explain what is CloudFront</summary><br><b>

AWS definition: "Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment."

More on CloudFront [here](https://aws.amazon.com/cloudfront)
</b></details>

<details>
<summary>Explain the following

  * Origin
  * Edge location
  * Distribution</summary><br><b>
</b></details>

#### AWS Monitoring & Logging

<details>
<summary>What is AWS CloudWatch?</summary><br><b>

AWS definition: "Amazon CloudWatch is a monitoring and observability service..."

More on CloudWatch [here](https://aws.amazon.com/cloudwatch)
</b></details>

<details>
<summary>What is AWS CloudTrail?</summary><br><b>

AWS definition: "AWS CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of your AWS account."

Read more on CloudTrail [here](https://aws.amazon.com/cloudtrail)
</b></details>

<details>
<summary>What is Simply Notification Service?</summary><br><b>

AWS definition: "a highly available, durable, secure, fully managed pub/sub messaging service that enables you to decouple microservices, distributed systems, and serverless applications."

Read more about it [here](https://aws.amazon.com/sns)
</b></details>

<details>
<summary>Explain the following in regards to SNS:

  * Topics
  * Subscribers
  * Publishers</summary><br><b>

  * Topics - used for grouping multiple endpoints
  * Subscribers - the endpoints where topics send messages to 
  * Publishers - the provider of the message (event, person, ...)
</b></details>

#### AWS Security 

<details>
<summary>What is the shared responsibility model? What AWS is responsible for and what the user is responsible for based on the shared responsibility model?</summary><br><b>

The shared responsibility model defines what the customer is responsible for and what AWS is responsible for.

More on the shared responsibility model [here](https://aws.amazon.com/compliance/shared-responsibility-model)
</b></details>

<details>
<summary>What is the AWS compliance program?</summary><br><b>
</b></details>

<details>
<summary>Explain what each of the following services is used for

  * AWS Inspector
  * AWS Artifact
  * AWS GuardDuty
  * AWS Shield</summary><br><b>
</b></details>

<details>
<summary>What is AWS WAF? Give an example of how it can used and describe what resources or services you can use it with</summary><br><b>
</b></details>

<details>
<summary>What AWS VPN is used for?</summary><br><b>
</b></details>

<details>
<summary>What is the difference between Site-to-Site VPN and Client VPN?</summary><br><b>
</b></details>

<details>
<summary>True or False? AWS Inspector can perform both network and host assessments</summary><br><b>

True
</b></details>

<details>
<summary>What is AWS Key Management Service (KMS)?</summary><br><b>

AWS definition: "KMS makes it easy for you to create and manage cryptographic keys and control their use across a wide range of AWS services and in your applications."
More on KMS [here](https://aws.amazon.com/kms)
</b></details>

#### AWS Databases

<details>
<summary>What is AWS RDS?</summary><br><b>
</b></details>

<details>
<summary>What is AWS DynamoDB?</summary><br><b>
</b></details>

<details>
<summary>What is AWS Redshift and how is it different than RDS?</summary><br><b>
</b></details>

<details>
<summary>What is AWS ElastiCache? For what cases is it used?</summary><br><b>

Amazon Elasticache is a fully managed Redis or Memcached in-memory data store.                                                                       
It's great for use cases like two-tier web applications where the most frequently accesses data is stored in ElastiCache so response time is optimal.
</b></details>

<details>
<summary>What is Amazon Aurora</summary><br><b>

A MySQL & Postgresql based relational database. Also, the default database proposed for the user when using RDS for creating a database.
Great for use cases like two-tier web applications that has a MySQL or Postgresql database layer and you need automated backups for your application.
</b></details>

### Final Note

Good luck! You can do it :)
