## AWS

### AWS Exercises

#### AWS - IAM

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Create a User | IAM | [Exercise](create_user.md) | [Solution](solutions/create_user.md) | Easy |
| Password Policy | IAM | [Exercise](password_policy_and_mfa.md) | [Solution](solutions/password_policy_and_mfa.md) | Easy |
| Create a role | IAM | [Exercise](create_role.md) | [Solution](solutions/create_role.md) | Easy |
| Credential Report | IAM | [Exercise](credential_report.md) | [Solution](solutions/credential_report.md) | Easy |
| Access Advisor | IAM | [Exercise](access_advisor.md) | [Solution](solutions/access_advisor.md) | Easy |

#### AWS - EC2

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Launch EC2 web instance | EC2 | [Exercise](launch_ec2_web_instance.md) | [Solution](solutions/launch_ec2_web_instance.md) | Easy |
| Security Groups | EC2 | [Exercise](security_groups.md) | [Solution](solutions/security_groups.md) | Easy |
| IAM Roles | EC2, IAM | [Exercise](ec2_iam_roles.md) | [Solution](solutions/ec2_iam_roles.md) | Easy |
| Spot Instances | EC2 | [Exercise](create_spot_instances.md) | [Solution](solutions/create_spot_instances.md) | Easy |
| Elastic IP | EC2, Networking | [Exercise](elastic_ip.md) | [Solution](solutions/elastic_ip.md) | Easy |
| Placement Groups Creation | EC2, Placement Groups | [Exercise](placement_groups.md) | [Solution](solutions/placement_groups.md) | Easy |
| Elastic Network Interfaces | EC2, ENI | [Exercise](elastic_network_interfaces.md) | [Solution](solutions/elastic_network_interfaces.md) | Easy |

#### AWS - Lambda

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Hello Function | Lambda | [Exercise](hello_function.md) | [Solution](solutions/hello_function.md) | Easy |
| URL Function | Lambda | [Exercise](url_function.md) | [Solution](solutions/url_function.md) | Easy |

#### AWS - Misc

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Budget Setup | Budget | [Exercise](budget_setup.md) | [Solution](solutions/budget_setup.md) | Easy |
| No Application :'( | Troubleshooting | [Exercise](no_application.md) | [Solution](solutions/no_application.md) | Easy |

### AWS Self Assessment

#### AWS - Global Infrastructure

<details>
<summary>Explain the following

  * Availability zone
  * Region
  * Edge location</summary><br><b>

AWS regions are data centers hosted across different geographical locations worldwide.<br>

Within each region, there are multiple isolated locations known as Availability Zones. Each availability zone is one or more data-centers with redundant network and connectivity and power supply. Multiple availability zones ensure high availability in case one of them goes down.<br>

Edge locations are basically content delivery network which caches data and insures lower latency and faster delivery to the users in any location. They are located in major cities in the world.
</b></details>

<details>
<summary>True or False? Each AWS region is designed to be completely isolated from the other AWS regions </summary><br><b>

True.
</b></details>

<details>
<summary>True or False? Each region has a minimum number of 1 availability zones and the maximum is 4</summary><br><b>

False. The minimum is 2 while the maximum is 6.
</b></details>

<details>
<summary>What considerations to take when choosing an AWS region for running a new application?</summary><br><b>

* Services Availability: not all service (and all their features) are available in every region
* Reduced latency: deploy application in a region that is close to customers
* Compliance: some countries have more strict rules and requirements such as making sure the data stays within the borders of the country or the region. In that case, only specific region can be used for running the application
* Pricing: the pricing might not be consistent across regions so, the price for the same service in different regions might be different.
</b></details>

#### AWS - IAM

<details>
<summary>What is IAM? What are some of its features?</summary><br><b>

In short, it's used for managing users, groups, access policies & roles
Full explanation can be found [here](https://aws.amazon.com/iam)
</b></details>

<details>
<summary>True or False? IAM configuration is defined globally and not per region</summary><br><b>

True
</b></details>

<details>
<summary>True or False? When creating an AWS account, root account is created by default. This is the recommended account to use and share in your organization</summary><br><b>

False. Instead of using the root account, you should be creating users and use them.
</b></details>

<details>
<summary>True or False? Groups in AWS IAM, can contain only users and not other groups</summary><br><b>

True
</b></details>

<details>
<summary>True or False? Users in AWS IAM, can belong only to a single group</summary><br><b>

False. Users can belong to multiple groups.
</b></details>

<details>
<summary>What are some best practices regarding IAM in AWS?</summary><br><b>

* Delete root account access keys and don't use root account regularly
* Create IAM user for any physical user. Don't share users.
* Apply "least privilege principle": give users only the permissions they need, nothing more than that.
* Set up MFA and consider enforcing using it
* Make use of groups to assign permissions ( user -> group -> permissions )
</b></details>

<details>
<summary>What permissions does a new user have?</summary><br><b>

Only a login access.
</b></details>

<details>
<summary>True or False? If a user in AWS is using password for authenticating, he doesn't needs to enable MFA</summary><br><b>

False(!). MFA is a great additional security layer to use for authentication.
</b></details>

<details>
<summary>What ways are there to access AWS?</summary><br><b>

  * AWS Management Console
  * AWS CLI
  * AWS SDK
</b></details>

<details>
<summary>What are Roles?</summary><br><b>

[AWS docs](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html): "An IAM role is an IAM identity that you can create in your account that has specific permissions...it is an AWS identity with permission policies that determine what the identity can and cannot do in AWS."
For example, you can make use of a role which allows EC2 service to access s3 buckets (read and write).
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

  - Grant access between two services/resources?
  - Grant user access to resources/services?</summary><br><b>

  * Role
  * Policy
</b></details>

<details>
<summary>What statements AWS IAM policies are consist of?</summary><br><b>

* Sid: identifier of the statement (optional)
* Effect: allow or deny access
* Action: list of actions (to deny or allow)
* Resource: a list of resources to which the actions are applied
* Principal: role or account or user to which to apply the policy
* Condition: conditions to determine when the policy is applied (optional)
</b></details>

<details>
<summary>Explain the following policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect:": "Allow",
            "Action": "*",
            "Resources": "*"
        }
    ]
}
```
</summary><br><b>

This policy permits to perform any action on any resource. It happens to be the "AdministratorAccess" policy.
</b></details>

<details>
<summary>What security tools AWS IAM provides?</summary><br><b>

* IAM Credentials Report: lists all the account users and the status of their credentials
* IAM Access Advisor: Shows service permissions granted to a user and information on when he accessed these services the last time
</b></details>

<details>
<summary>Which tool would you use to optimize user permissions by identifying which services he doesn't regularly (or at all) access?</summary><br><b>

IAM Access Advisor
</b></details>

#### AWS - EC2

<details>
<summary>What is EC2?</summary><br><b>

"a web service that provides secure, resizable compute capacity in the cloud".
Read more [here](https://aws.amazon.com/ec2)
</b></details>

<details>
<summary>True or False? EC2 is a regional service</summary><br><b>

True. As opposed to IAM for example, which is a global service, EC2 is a regional service.
</b></details>

<details>
<summary>What are some of the properties/configuration options of EC2 instances that can be set or modified?</summary><br><b>

* OS (Linux, Windows)
* RAM and CPU
* Networking - IP, Card properties like speed
* Storage Space - (EBS, EFS, EC2 Instance Store)
* EC2 User Data
* Security groups
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
<summary>What is an instance type?</summary><br><b>

"the instance type that you specify determines the hardware of the host computer used for your instance"
Read more about instance types [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html)
</b></details>

<details>
<summary>Explain the instance type naming convention</summary><br><b>

Let's take for example the following instance type: m5.large

`m` is the instance class
`5` is the generation
`large` is the size of the instance (affects the spec properties like vCPUs and RAM)
</b></details>

<details>
<summary>True or False? The following are instance types available for a user in AWS:

  * Compute optimizied
  * Network optimizied
  * Web optimized</summary><br><b>

False. From the above list only compute optimized is available.
</b></details>

<details>
<summary>Explain each of the following instance types:

  * "Compute Optimized"
  * "Memory Optimized"
  * "Storage Optimized"</summary><br><b>

Compute Optimized:

* Used for compute-intensive tasks
* It has high performance processors
* Use cases vary: gaming serves, machine learning, batch processing, etc.

Memory Optimized:

* Used for processing large data sets in memory
* Other use cases: high performance, databases, distributed cache stores

Storage Optimized:

* Used for storage intensive tasks - high read and write access to large data sets
* Use cases: databases, OLTP system, distributing file systems
</b></details>

<details>
<summary>What can you attach to an EC2 instance in order to store data?</summary><br><b>

EBS
</b></details>

##### AWS EC2 - EBS

<details>
<summary>What is EBS?</summary><br><b>

"provides block level storage volumes for use with EC2 instances. EBS volumes behave like raw, unformatted block devices."
More on EBS [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)
</b></details>

<details>
<summary>What happens to EC2 disk (EBS) when the instance is terminated?</summary><br><b>

All the related EBS volumes are removed and data is lost.
</b></details>

<details>
<summary>What happens to the EC2 disk (EBS) when the instance is stopped?</summary><br><b>

Disk is intact and can be used when the instance starts.
</b></details>

<details>
<summary>What EC2 pricing models are there?</summary><br><b>

On Demand - pay a fixed rate by the hour/second with no commitment. You can provision and terminate it at any given time.
Reserved - you get capacity reservation, basically purchase an instance for a fixed time of period. The longer, the cheaper.
Spot - Enables you to bid whatever price you want for instances or pay the spot price.
Dedicated Hosts - physical EC2 server dedicated for your use.
</b></details>

<details>
<summary>True or False? Reserved instance has to be used for a minimum of 1 year</summary><br><b>

True.
</b></details>

<details>
<summary>Explain the following types of reserved instances:

  * Convertible Reserved Instances
  * Scheduled Reserved Instances</summary><br><b>

* Convertible Reserved Instances: used for long running workloads but used when instance type might change during the period of time it's resreved
* Scheduled Reserved Instances: when you need to reserve an instance for a long period but you don't need it continuously (so for example you need it only in the morning)
</b></details>

<details>
<summary>True or False? In EC2 On Demand, you pay per hour when using Linux or Windows and per second (after first minute) when using any other operating system</summary><br><b>

False. You pay per second (after the first minute) when using Windows or Linux and per hour for any other OS.
</b></details>

<details>
<summary>You need an instance for short-term and the workload running on instance must not be interrupted. Which pricing model would you use?</summary><br><b>

On Demand is good for short-term non-interrupted workloads (but it also has the highest cost).
</b></details>

<details>
<summary>You need an instance for running an application for a period of 2 years continuously, without changing instance type. Which pricing model would you use?</summary><br><b>

Reserved instances: they are cheaper than on-demand and the instance is yours for the chosen period of time.
</b></details>

<details>
<summary>Which pricing model has potentially the biggest discount and what its advantage</summary><br><b>

Spot instances provide the biggest discount but has the disadvantage of risking losing them due bigger bid price.
</b></details>

<details>
<summary>You need an instance for two years, but only between 10:00-15:00 every day. Which pricing model would you use?</summary><br><b>

Reserved instances from the "Scheduled Reserved Instances" type which allows you to reserve for specific time window (like 10:00-15:00 every day).
</b></details>

<details>
<summary>You need an instance for running workloads. You don't care if they fail for a given moment as long as they run eventually. Which pricing model would you use?</summary><br><b>

Spot instances. The discount potential is the highest compared to all other pricing models. The disadvantage is that you can lose the instance at any point so, you must run only workloads that you are fine with them failing suddenly.
</b></details>

<details>
<summary>You need a physical server only for your use. Which pricing model are you going to use?</summary><br><b>

EC2 Dedicated Host
</b></details>

<details>
<summary>What are some of the differences between dedicated hosts and dedicated instances?</summary><br><b>

In dedicated hosts you have per host billing, you have more visibility (sockets, cores, ...) and you can control where instance will be placed.<br>
In dedicated instances the billing is per instance but you can't control placement and you don't have visibility of sockets, cores, ...
</b></details>

<details>
<summary>For what use cases, EC2 dedicated hosts are useful for?</summary><br><b>

* Compliance needs
* When the software license is complex (Bring Your Own License) and doesn't support cloud or multi-tenants
* Regulatory requirements
</b></details>

<details>
<summary>What are Security Groups?</summary><br><b>

"A security group acts as a virtual firewall that controls the traffic for one or more instances"
More on this subject [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)
</b></details>

<details>
<summary>True or False? Security groups only contain deny rules</summary><br><b>

False. Security groups only contain allow rules.
</b></details>

<details>
<summary>True or False? One security group can be attached to multiple instances</summary><br><b>

True
</b></details>

<details>
<summary>True or False? Security groups are not locked down to a region and VPC (meaning you don't have to create a new one when switching regions)</summary><br><b>

False. They are locked down to regions and VPC.
</b></details>

<details>
<summary>True or False? By default, when using security groups, all inbound traffic to an EC2 instance is blocked and all outbound traffic is allowed</summary><br><b>

True
</b></details>

<details>
<summary>What is the advantage of referencing security groups from a given security group?</summary><br><b>

Imagine you have an instance referencing two security groups, allowing to get inbound traffic from them.<br>
Now imagine you have two instances, each using one of the security groups referenced in the instance we've just mentioned. This means you can get traffic from these two instances because they use security groups which referenced in the instance mentioned at the beginning. No need to use IPs.
</b></details>

<details>
<summary>How to migrate an instance to another availability zone?</summary><br><b>
</b></details>

<details>
<summary>What can you attach to an EC2 instance in order to store data?</summary><br><b>

EBS
</b></details>

<details>
<summary>What EC2 reserved instance types are there?</summary><br><b>

Standard RI - most significant discount + suited for steady-state usage
Convertible RI - discount + change attribute of RI + suited for steady-state usage
Scheduled RI - launch within time windows you reserve

Learn more about EC2 RI [here](https://aws.amazon.com/ec2/pricing/reserved-instances)
</b></details>

<details>
<summary>For how long can reserved instances be reserved?</summary><br><b>

1 or 3 years.
</b></details>

<details>
<summary>What allows you to control inbound and outbound instance traffic?</summary><br><b>

Security Groups
</b></details>

<details>
<summary>What bootstrapping means and how to use it in AWS EC2?</summary><br><b>

Bootstrapping is about launching commands when a machine starts for the first time.
In AWS EC2 this is done using the EC2 user data script.
</b></details>

<details>
<summary>You get time out when trying reach your application which runs on an EC2 instance. Specify one reason why it would possibly happen</summary><br><b>

Security group isn't configured properly.
</b></details>

<details>
<summary>What is the AWS Instance Connect?</summary><br><b>

[AWS](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Connect-using-EC2-Instance-Connect.html): "Amazon EC2 Instance Connect provides a simple and secure way to connect to your Linux instances using Secure Shell (SSH)."
</b></details>

<details>
<summary>You try to run EC2 commands in an EC2 instance you've just created but it fails due to missing credentials. What would you do?</summary><br><b>

DO NOT configure AWS credentials on the instance (this means anyone else in your account would be able to use and see your credentials).<br>
The best practice is to attach an IAM role with sufficient permissions (like `IAMReadOnlyAccess`)
</b></details>

<details>
<summary>True or False? Cancelling a Spot instance request terminates the instance</summary><br><b>

False. When you cancel a Spot instance request, you are not terminating the instances created by it.<br>
To terminate such instances, you must cancel the Spot instance request first.
</b></details>

<details>
<summary>What are Spot Flees?</summary><br><b>

Set of Spot instance and if you want, also on-demand instances.
</b></details>

<details>
<summary>What strategies are there to allocate Spot instances?</summary><br><b>

* lowestPrice: launch instances from the pool that has the lowest price
* diversified: distributed across all pools
* capacityOptimized: optimized based on the number of instances
</b></details>

<details>
<summary>From networking perspective, what do you get by default when running an EC2 instance?</summary><br><b>

A private IP and a public IP.
</b></details>

<details>
<summary>What happens when you hibernate an EC2 instance?</summary><br><b>

[AWS Docs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Hibernate.html: "Hibernation saves the contents from the instance memory (RAM) to your Amazon Elastic Block Store (Amazon EBS) root volume."
</b></details>

<details>
<summary>True or False? Using EC2 hibernate option results in having faster instance boot</summary><br><b>

True. This is because the operating system isn't restarted or stopped.
</b></details>

#### AWS - Lambda

<details>
<summary>Explain what is AWS Lambda</summary><br><b>

AWS definition: "AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume."

Read more on it [here](https://aws.amazon.com/lambda)
</b></details>

<details>
<summary>True or False? In AWS Lambda, you are charged as long as a function exists, regardless of whether it's running or not</summary><br><b>

False. Charges are being made when the code is executed.
</b></details>

<details>
<summary>Which of the following set of languages Lambda supports?

- R, Swift, Rust, Kotlin
- Python, Ruby, Go
- Python, Ruby, PHP
</summary><br><b>

- Python, Ruby, Go
</b></details>

<details>
<summary>True or False? Basic lambda permissions allow you only to upload logs to Amazon CloudWatch Logs</summary><br><b>

True
</b></details>

#### AWS Containers

<details>
<summary>What is Amazon ECS?</summary><br><b>

Amazon definition: "Amazon Elastic Container Service (Amazon ECS) is a fully managed container orchestration service. Customers such as Duolingo, Samsung, GE, and Cook Pad use ECS to run their most sensitive and mission critical applications because of its security, reliability, and scalability."

Learn more [here](https://aws.amazon.com/ecs)
</b></details>

<details>
<summary>What is Amazon ECR?</summary><br><b>

Amazon definition: "Amazon Elastic Container Registry (ECR) is a fully-managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images."

Learn more [here](https://aws.amazon.com/ecr)
</b></details>

<details>
<summary>What is AWS Fargate?</summary><br><b>

Amazon definition: "AWS Fargate is a serverless compute engine for containers that works with both Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS)."

Learn more [here](https://aws.amazon.com/fargate)
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

  - Object Lifecycles
  - Object Sharing
  - Object Versioning</summary><br><b>

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
<summary>A customer would like to move data which is rarely accessed from standard storage class to the most cheapest class there is. Which storage class should be used?

  * One Zone-IA
  * Glacier Deep Archive
  * Intelligent-Tiering</summary><br><b>

Glacier Deep Archive
</b></details>

<details>
<summary>What Glacier retrieval options are available for the user?</summary><br><b>

Expedited, Standard and Bulk
</b></details>

<details>
<summary>True or False? Each AWS account can store up to 500 PetaByte of data. Any additional storage will cost double</summary><br><b>

False. Unlimited capacity.
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

<details>
<summary>What is "Amazon S3 Transfer Acceleration"?</summary><br><b>

AWS definition: "Amazon S3 Transfer Acceleration enables fast, easy, and secure transfers of files over long distances between your client and an S3 bucket"

Learn more [here](https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html)
</b></details>

<details>
<summary>Explain data consistency</summary><br><b>
	S3 Data Consistency provides strong read-after-write consistency for PUT and DELETE requests of objects in the S3 bucket in all AWS Regions. S3 always return latest file version.
</b></details>

<details>
<summary>Can you host dynamic websites on S3? What about static websites?</summary><br><b>
	No. S3 support only statis hosts. On a static website, individual webpages include static content. They might also contain client-side scripts. By contrast, a dynamic website relies on server-side processing, including server-side scripts such as PHP, JSP, or ASP.NET. Amazon S3 does not support server-side scripting.
</b></details>

<details>
<summary>What security measures have you taken in context of S3?</summary><br><b>
	* Enable versioning.
	* Don't make bucket public.
	* Enable encryption if it's disabled.
</b></details>

<details>
<summary>What storage options are there for EC2 Instances?</summary><br><b>
</b></details>

<details>
<summary>What is Amazon EFS?</summary><br><b>

Amazon definition: "Amazon Elastic File System (Amazon EFS) provides a simple, scalable, fully managed elastic NFS file system for use with AWS Cloud services and on-premises resources."

Learn more [here](https://aws.amazon.com/efs)
</b></details>

<details>
<summary>What is AWS Snowmobile?</summary><br><b>

"AWS Snowmobile is an Exabyte-scale data transfer service used to move extremely large amounts of data to AWS."

Learn more [here](https://aws.amazon.com/snowmobile)
</b></details>

#### AWS Disaster Recovery

<details>
<summary>In regards to disaster recovery, what is RTO and RPO?</summary><br><b>

RTO - The maximum acceptable length of time that your application can be offline.

RPO - The maximum acceptable length of time during which data might be lost from your application due to an incident.
</b></details>

<details>
<summary>What types of disaster recovery techniques AWS supports?</summary><br><b>

* The Cold Method - Periodically backups and sending the backups off-site<br>
* Pilot Light - Data is mirrored to an environment which is always running
* Warm Standby - Running scaled down version of production environment
* Multi-site - Duplicated environment that is always running
</b></details>

<details>
<summary>Which disaster recovery option has the highest downtime and which has the lowest?</summary><br><b>

Lowest - Multi-site
Highest - The cold method
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

<details>
<summary>What delivery methods available for the user with CDN?</summary><br><b>
</b></details>

<details>
<summary>True or False?. Objects are cached for the life of TTL</summary><br><b>

True
</b></details>

<details>
<summary>What is AWS Snowball?</summary><br><b>

A transport solution which was designed for transferring large amounts of data (petabyte-scale) into and out the AWS cloud.
</b></details>

##### AWS ELB

<details>
<summary>What is ELB (Elastic Load Balancing)?</summary><br><b>

AWS definition: "Elastic Load Balancing automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions."

More on ELB [here](https://aws.amazon.com/elasticloadbalancing)
</b></details>

<details>
<summary>What types of load balancers are supported in EC2 and what are they used for?</summary><br><b>

  * Application LB - layer 7 traffic
  * Network LB - ultra-high performances or static IP address (layer 4)
  * Classic LB - low costs, good for test or dev environments (retired by August 15, 2022)
  * Gateway LB - transparent network gateway and and distributes traffic such as firewalls, intrusion detection and prevention systems, and deep packet inspection systems. (layer 3)
</b></details>

#### AWS Security

<details>
<summary>What is the shared responsibility model? What AWS is responsible for and what the user is responsible for based on the shared responsibility model?</summary><br><b>

The shared responsibility model defines what the customer is responsible for and what AWS is responsible for.

More on the shared responsibility model [here](https://aws.amazon.com/compliance/shared-responsibility-model)
</b></details>

<details>
<summary>True or False? Based on the shared responsibility model, Amazon is responsible for physical CPUs and security groups on instances</summary><br><b>

False. It is responsible for Hardware in its sites but not for security groups which created and managed by the users.
</b></details>

<details>
<summary>Explain "Shared Controls" in regards to the shared responsibility model</summary><br><b>

AWS definition: "apply to both the infrastructure layer and customer layers, but in completely separate contexts or perspectives. In a shared control, AWS provides the requirements for the infrastructure and the customer must provide their own control implementation within their use of AWS services"

Learn more about it [here](https://aws.amazon.com/compliance/shared-responsibility-model)
</b></details>

<details>
<summary>What is the AWS compliance program?</summary><br><b>
</b></details>

<details>
<summary>How to secure instances in AWS?</summary><br><b>

  * Instance IAM roles should have minimal permissions needed. You don't want an instance-level incident to become an account-level incident
  * Use "AWS System Manager Session Manager" for SSH
  * Using latest OS images with your instances
</b></details>

<details>
<summary>What is AWS Artifact?</summary><br><b>

AWS definition: "AWS Artifact is your go-to, central resource for compliance-related information that matters to you. It provides on-demand access to AWS’ security and compliance reports and select online agreements."

Read more about it [here](https://aws.amazon.com/artifact)
</b></details>

<details>
<summary>What is AWS Inspector?</summary><br><b>

AWS definition: "Amazon Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS. Amazon Inspector automatically assesses applications for exposure, vulnerabilities, and deviations from best practices.""

Learn more [here](https://aws.amazon.com/inspector)
</b></details>

<details>
<summary>What is AWS Guarduty?</summary><br><b>
AWS definition: "Amazon GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect your Amazon Web Services accounts, workloads, and data stored in Amazon S3" <br>
Monitor VPC Flow lows, DNS logs, CloudTrail S3 events and CloudTrail Mgmt events.
</b></details>

<details>
<summary>What is AWS Shield?</summary><br><b>

AWS definition: "AWS Shield is a managed Distributed Denial of Service (DDoS) protection service that safeguards applications running on AWS."
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
<summary>What is AWS CloudHSM?</summary><br><b>

Amazon definition: "AWS CloudHSM is a cloud-based hardware security module (HSM) that enables you to easily generate and use your own encryption keys on the AWS Cloud."

Learn more [here](https://aws.amazon.com/cloudhsm)
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

<details>
<summary>What is AWS Acceptable Use Policy?</summary><br><b>

It describes prohibited uses of the web services offered by AWS.
More on AWS Acceptable Use Policy [here](https://aws.amazon.com/aup)
</b></details>

<details>
<summary>True or False? A user is not allowed to perform penetration testing on any of the AWS services</summary><br><b>

False. On some services, like EC2, CloudFront and RDS, penetration testing is allowed.
</b></details>

<details>
<summary>True or False? DDoS attack is an example of allowed penetration testing activity</summary><br><b>

False.
</b></details>

<details>
<summary>True or False? AWS Access Key is a type of MFA device used for AWS resources protection</summary><br><b>

False. Security key is an example of an MFA device.
</b></details>

<details>
<summary>What is Amazon Cognito?</summary><br><b>

Amazon definition: "Amazon Cognito handles user authentication and authorization for your web and mobile apps."

Learn more [here](https://docs.aws.amazon.com/cognito/index.html)
</b></details>

<details>
<summary>What is AWS ACM?</summary><br><b>

Amazon definition: "AWS Certificate Manager is a service that lets you easily provision, manage, and deploy public and private Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services and your internal connected resources."

Learn more [here](https://aws.amazon.com/certificate-manager)
</b></details>

#### AWS Databases

<details>
<summary>What is AWS RDS?</summary><br><b>
</b></details>

<details>
<summary>What is AWS DynamoDB?</summary><br><b>
</b></details>

<details>
<summary>Explain "Point-in-Time Recovery" feature in DynamoDB</summary><br><b>

Amazon definition: "You can create on-demand backups of your Amazon DynamoDB tables, or you can enable continuous backups using point-in-time recovery. For more information about on-demand backups, see On-Demand Backup and Restore for DynamoDB."

Learn more [here](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery.html)
</b></details>

<details>
<summary>Explain "Global Tables" in DynamoDB</summary><br><b>

Amazon definition: "A global table is a collection of one or more replica tables, all owned by a single AWS account."

Learn more [here](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/V2globaltables_HowItWorks.html)
</b></details>

<details>
<summary>What is DynamoDB Accelerator?</summary><br><b>

Amazon definition: "Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, in-memory cache for DynamoDB that delivers up to a 10x performance improvement – from milliseconds to microseconds..."

Learn more [here](https://aws.amazon.com/dynamodb/dax)
</b></details>

<details>
<summary>What is AWS Redshift and how is it different than RDS?</summary><br><b>

cloud data warehouse
</b></details>

<details>
<summary>What do you if you suspect AWS Redshift performs slowly?</summary><br><b>

* You can confirm your suspicion by going to AWS Redshift console and see running queries graph. This should tell you if there are any long-running queries.
* If confirmed, you can query for running queries and cancel the irrelevant queries
* Check for connection leaks (query for running connections and include their IP)
* Check for table locks and kill irrelevant locking sessions
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

<details>
<summary>What is Amazon DocumentDB?</summary><br><b>

Amazon definition: "Amazon DocumentDB (with MongoDB compatibility) is a fast, scalable, highly available, and fully managed document database service that supports MongoDB workloads. As a document database, Amazon DocumentDB makes it easy to store, query, and index JSON data."

Learn more [here](https://aws.amazon.com/documentdb)
</b></details>

<details>
<summary>What "AWS Database Migration Service" is used for?</summary><br><b>
</b></details>

<details>
<summary>What type of storage is used by Amazon RDS?</summary><br><b>

EBS
</b></details>

<details>
<summary>Explain Amazon RDS Read Replicas</summary><br><b>

AWS definition: "Amazon RDS Read Replicas provide enhanced performance and durability for RDS database (DB) instances. They make it easy to elastically scale out beyond the capacity constraints of a single DB instance for read-heavy database workloads."
Read more about [here](https://aws.amazon.com/rds/features/read-replicas)
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

True. Just to clarify, a single subnet resides entirely in one AZ.
</b></details>

<details>
<summary>What is an Internet Gateway?</summary><br><b>

"component that allows communication between instances in your VPC and the internet" (AWS docs).
Read more about it [here](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html)
</b></details>

<details>
<summary>True or False? NACL allow or deny traffic on the subnet level</summary><br><b>

True
</b></details>

<details>
<summary>What is VPC peering?</summary><br><b>

[docs.aws](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html): "A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses or IPv6 addresses."
</b></details>

<details>
<summary>True or False? Multiple Internet Gateways can be attached to one VPC</summary><br><b>

False. Only one internet gateway can be attached to a single VPC.
</b></details>

<details>
<summary>What is an Elastic IP address?</summary><br><b>

[AWS Docs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html): "An Elastic IP address is a static IPv4 address designed for dynamic cloud computing. An Elastic IP address is allocated to your AWS account, and is yours until you release it. By using an Elastic IP address, you can mask the failure of an instance or software by rapidly remapping the address to another instance in your account."
</b></details>

<details>
<summary>True or False? When stopping and starting an EC2 instance, its public IP changes</summary><br><b>

True
</b></details>

<details>
<summary>What are the best practices around Elastic IP?</summary><br><b>

The best practice is actually not using them in the first place. It's more common to use a load balancer without a public IP or use a random public IP and register a DNS record to it
</b></details>

<details>
<summary>True or False? An Elastic IP is free, as long it's not associated with an EC2 instance</summary><br><b>

False. An Elastic IP is free of charge as long as **it is ** associated with an EC2 instance. This instance should be running and should have only one Elastic IP.
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

<details>
<summary>True or False? When you need a fixed public IP for your instance, you should use an Elastic IP</summary><br><b>

True
</b></details>

##### AWS EC2 - ENI

<details>
<summary>Explain Elastic Network Interfaces (ENI)</summary><br><b>

[AWS Docs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html): "An elastic network interface is a logical networking component in a VPC that represents a virtual network card."
</b></details>

<details>
<summary>Name at least three attributes the Elastic Network Interfaces (ENI) can include</summary><br><b>

1. One public IPv4 address
2. Mac Address
3. A primary private IPv4 address (from the address range of your VPC)
</b></details>

<details>
<summary>True or False? ENI are not bound to a specific availability zone</summary><br><b>

False. ENI are bound to specific availability zone.
</b></details>

<details>
<summary>True or False? ENI can be created independently of EC2 instances</summary><br><b>

True. They can be attached later on and on the fly (for failover purposes).
</b></details>

##### AWS EC2 - Placement Groups

<details>
<summary>What are "Placement Groups"?</summary><br><b>

[AWS Docs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html): "When you launch a new EC2 instance, the EC2 service attempts to place the instance in such a way that all of your instances are spread out across underlying hardware to minimize correlated failures. You can use placement groups to influence the placement of a group of interdependent instances to meet the needs of your workload."
</b></details>

<details>
<summary>What Placement Groups strategies are there?</summary><br><b>

* Cluster: places instance close together in an AZ.
* Spread: spreads the instance across the hardware
* Partition: spreads the instances across different partitions (= different sets of hardware/racks) within an AZ
</b></details>

<details>
<summary>For each of the following scenarios choose a placement group strategy:

  * High availability is top priority
  * Low latency between instances
  * Instances must be isolated from each other
  * Big Data applications that are partition aware
  * Big Data process that needs to end quickly</summary><br><b>

  * High availability is top priority - Spread
  * Low latency between instances - Cluster
  * Instances must be isolated from each other - Spread
  * Big Data applications that are partition aware - Partition
  * Big Data process that needs to end quickly - Cluster
</b></details>

<details>
<summary>What are the cons and pros of the "Cluster" placement group strategy?</summary><br><b> 

Cons: if the hardware fails, all instances fail
Pros: Low latency & high throughput network
</b></details>

<details>
<summary>What are the cons and pros of the "Spread" placement group strategy?</summary><br><b> 

Cons:
  * Current limitation is 7 instances per AZ (per replacement group)
Pros:
  * Maximized high availability (instances on different hardware, span across AZs)
</b></details>

#### AWS - Identify the service or tool

<details>
<summary>What would you use for automating code/software deployments?</summary><br><b>

AWS CodeDeploy
</b></details>

<details>
<summary>You would like to invoke a function every time you enter a URL in the browser. Which service would you use for that?</summary><br><b>

AWS Lambda
</b></details>

<details>
<summary>What would you use for easily creating similar AWS environments/resources for different customers?</summary><br><b>

CloudFormation
</b></details>

<details>
<summary>Using which service, can you add user sign-up, sign-in and access control to mobile and web apps?</summary><br><b>

Cognito
</b></details>

<details>
<summary>Which service would you use for building a website or web application?</summary><br><b>

Lightsail
</b></details>

<details>
<summary>Which tool would you use for choosing between Reserved instances or On-Demand instances?</summary><br><b>

Cost Explorer
</b></details>

<details>
<summary>What would you use to check how many unassociated Elastic IP address you have?</summary><br><b>

Trusted Advisor
</b></details>

<details>
<summary>Which service allows you to transfer large amounts (Petabytes) of data in and out of the AWS cloud?</summary><br><b>

AWS Snowball
</b></details>

<details>
<summary>Which service would you use if you need a data warehouse?</summary><br><b>

AWS RedShift
</b></details>

<details>
<summary>Which service provides a virtual network dedicated to your AWS account?</summary><br><b>

VPC
</b></details>

<details>
<summary>What you would use for having automated backups for an application that has MySQL database layer?</summary><br><b>

Amazon Aurora
</b></details>

<details>
<summary>What would you use to migrate on-premise database to AWS?</summary><br><b>

AWS Database Migration Service (DMS)
</b></details>

<details>
<summary>What would you use to check why certain EC2 instances were terminated?</summary><br><b>

AWS CloudTrail
</b></details>

<details>
<summary>What would you use for SQL database?</summary><br><b>

AWS RDS
</b></details>

<details>
<summary>What would you use for NoSQL database?</summary><br><b>

AWS DynamoDB
</b></details>

<details>
<summary>What would you use for adding image and video analysis to your application?</summary><br><b>

AWS Rekognition
</b></details>

<details>
<summary>Which service would you use for debugging and improving performances issues with your applications?</summary><br><b>

AWS X-Ray
</b></details>

<details>
<summary>Which service is used for sending notifications?</summary><br><b>

SNS
</b></details>

<details>
<summary>What would you use for running SQL queries interactively on S3?</summary><br><b>

AWS Athena
</b></details>

<details>
<summary>What would you use for preparing and combining data for analytics or ML?</summary><br><b>

AWS Glue
</b></details>

<details>
<summary>Which service would you use for monitoring malicious activity and unauthorized behavior in regards to AWS accounts and workloads?</summary><br><b>

Amazon GuardDuty
</b></details>

<details>
<summary>Which service would you use for centrally manage billing, control access, compliance, and security across multiple AWS accounts?</summary><br><b>

AWS Organizations
</b></details>

<details>
<summary>Which service would you use for web application protection?</summary><br><b>

AWS WAF
</b></details>

<details>
<summary>You would like to monitor some of your resources in the different services. Which service would you use for that?</summary><br><b>

CloudWatch
</b></details>

<details>
<summary>Which service would you use for performing security assessment?</summary><br><b>

AWS Inspector
</b></details>

<details>
<summary>Which service would you use for creating DNS record?</summary><br><b>

Route 53
</b></details>

<details>
<summary>What would you use if you need a fully managed document database?</summary><br><b>

Amazon DocumentDB
</b></details>

<details>
<summary>Which service would you use to add access control (or sign-up, sign-in forms) to your web/mobile apps?</summary><br><b>

AWS Cognito
</b></details>

<details>
<summary>Which service would you use if you need messaging queue?</summary><br><b>

Simple Queue Service (SQS)
</b></details>

<details>
<summary>Which service would you use if you need managed DDOS protection?</summary><br><b>

AWS Shield
</b></details>

<details>
<summary>Which service would you use if you need store frequently used data for low latency access?</summary><br><b>

ElastiCache
</b></details>

<details>
<summary>What would you use to transfer files over long distances between a client and an S3 bucket?</summary><br><b>

Amazon S3 Transfer Acceleration
</b></details>

<details>
<summary>Which service would you use for distributing incoming requests across multiple?</summary><br><b>

Route 53
</b></details>

<details>
<summary>Which services are involved in getting a custom string (based on the input) when inserting a URL in the browser?</summary><br><b>

Lambda - to define a function that gets an input and returns a certain string<br>
API Gateway - to define the URL trigger (= when you insert the URL, the function is invoked).
</b></details>

<details>
<summary>Which service would you use for data or events streaming?</summary><br><b>

Kinesis
</b></details>

#### AWS DNS

<details>
<summary>What is Route 53?</summary><br><b>

"Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service..."
Some of Route 53 features:
  * Register domain
  * DNS service - domain name translations
  * Health checks - verify your app is available

More on Route 53 [here](https://aws.amazon.com/route53)
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

  - Topics
  - Subscribers
  - Publishers</summary><br><b>

  * Topics - used for grouping multiple endpoints
  * Subscribers - the endpoints where topics send messages to
  * Publishers - the provider of the message (event, person, ...)
</b></details>

#### AWS Billing & Support

<details>
<summary>What is AWS Organizations?</summary><br><b>

AWS definition: "AWS Organizations helps you centrally govern your environment as you grow and scale your workloads on AWS."
More on Organizations [here](https://aws.amazon.com/organizations)
</b></details>

<details>
<summary>What are Service Control Policies and to what service they belong?</summary><br><b>

AWS organizations service and the definition by Amazon: "SCPs offer central control over the maximum available permissions for all accounts in your organization, allowing you to ensure your accounts stay within your organization’s access control guidelines."

Learn more [here](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html)
</b></details>

<details>
<summary>Explain AWS pricing model</summary><br><b>

It mainly works on "pay-as-you-go" meaning you pay only for what are using and when you are using it.
In s3 you pay for 1. How much data you are storing 2. Making requests (PUT, POST, ...)
In EC2 it's based on the purchasing option (on-demand, spot, ...), instance type, AMI type and the region used.

More on AWS pricing model [here](https://aws.amazon.com/pricing)
</b></details>

<details>
<summary>How one should estimate AWS costs when for example comparing to on-premise solutions?</summary><br><b>

* TCO calculator
* AWS simple calculator
* Cost Explorer
</b></details>

<details>
<summary>What basic support in AWS includes?</summary><br><b>

* 24x7 customer service
* Trusted Advisor
* AWS personal Health Dashoard
</b></details>

<details>
<summary>How are EC2 instances billed?</summary><br><b>
</b></details>

<details>
<summary>What AWS Pricing Calculator is used for?</summary><br><b>
</b></details>

<details>
<summary>What is Amazon Connect?</summary><br><b>

Amazon definition: "Amazon Connect is an easy to use omnichannel cloud contact center that helps companies provide superior customer service at a lower cost."

Learn more [here](https://aws.amazon.com/connect)
</b></details>

<details>
<summary>What are "APN Consulting Partners"?</summary><br><b>

Amazon definition: "APN Consulting Partners are professional services firms that help customers of all types and sizes design, architect, build, migrate, and manage their workloads and applications on AWS, accelerating their journey to the cloud."

Learn more [here](https://aws.amazon.com/partners/consulting)
</b></details>

<details>
<summary>Which of the following are AWS accounts types (and are sorted by order)?

  - Basic, Developer, Business, Enterprise
  - Newbie, Intermediate, Pro, Enterprise
  - Developer, Basic, Business, Enterprise
  - Beginner, Pro, Intermediate Enterprise
  </summary><br><b>

  - Basic, Developer, Business, Enterprise
</b></details>

<details>
<summary>True or False? Region is a factor when it comes to EC2 costs/pricing</summary><br><b>

True. You pay differently based on the chosen region.
</b></details>

<details>
<summary>What is "AWS Infrastructure Event Management"?</summary><br><b>

AWS Definition: "AWS Infrastructure Event Management is a structured program available to Enterprise Support customers (and Business Support customers for an additional fee) that helps you plan for large-scale events such as product or application launches, infrastructure migrations, and marketing events."
</b></details>

#### AWS Automation

<details>
<summary>What is AWS CodeDeploy?</summary><br><b>

Amazon definition: "AWS CodeDeploy is a fully managed deployment service that automates software deployments to a variety of compute services such as Amazon EC2, AWS Fargate, AWS Lambda, and your on-premises servers."

Learn more [here](https://aws.amazon.com/codedeploy)
</b></details>

<details>
<summary>Explain what is CloudFormation</summary><br><b>
</b></details>

#### AWS - Misc

<details>
<summary>Which AWS service you have experience with that you think is not very common?</summary><br><b>
</b></details>

<details>
<summary>What is AWS CloudSearch?</summary><br><b>
</b></details>

<details>
<summary>What is AWS Lightsail?</summary><br><b>

AWS definition: "Lightsail is an easy-to-use cloud platform that offers you everything needed to build an application or website, plus a cost-effective, monthly plan."
</b></details>

<details>
<summary>What is AWS Rekognition?</summary><br><b>

AWS definition: "Amazon Rekognition makes it easy to add image and video analysis to your applications using proven, highly scalable, deep learning technology that requires no machine learning expertise to use."

Learn more [here](https://aws.amazon.com/rekognition)
</b></details>

<details>
<summary>What AWS Resource Groups used for?</summary><br><b>

Amazon definition: "You can use resource groups to organize your AWS resources. Resource groups make it easier to manage and automate tasks on large numbers of resources at one time. "

Learn more [here](https://docs.aws.amazon.com/ARG/latest/userguide/welcome.html)
</b></details>

<details>
<summary>What is AWS Global Accelerator?</summary><br><b>

Amazon definition: "AWS Global Accelerator is a service that improves the availability and performance of your applications with local or global users..."

Learn more [here](https://aws.amazon.com/global-accelerator)
</b></details>

<details>
<summary>What is AWS Config?</summary><br><b>

Amazon definition: "AWS Config is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources."

Learn more [here](https://aws.amazon.com/config)
</b></details>

<details>
<summary>What is AWS X-Ray?</summary><br><b>

AWS definition: "AWS X-Ray helps developers analyze and debug production, distributed applications, such as those built using a microservices architecture."
Learn more [here](https://aws.amazon.com/xray)
</b></details>

<details>
<summary>What is AWS OpsWorks?</summary><br><b>

Amazon definition: "AWS OpsWorks is a configuration management service that provides managed instances of Chef and Puppet."

Learn more about it [here](https://aws.amazon.com/opsworks)
</b></details>

<details>
<summary>What is AWS Athena?</summary><br><b>

"Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL."

Learn more about AWS Athena [here](https://aws.amazon.com/athena)
</b></details>

<details>
<summary>What is Amazon Cloud Directory?</summary><br><b>

Amazon definition: "Amazon Cloud Directory is a highly available multi-tenant directory-based store in AWS. These directories scale automatically to hundreds of millions of objects as needed for applications."

Learn more [here](https://docs.aws.amazon.com/clouddirectory/latest/developerguide/what_is_cloud_directory.html)
</b></details>

<details>
<summary>What is AWS Elastic Beanstalk?</summary><br><b>

AWS definition: "AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services...You can simply upload your code and Elastic Beanstalk automatically handles the deployment"

Learn more about it [here](https://aws.amazon.com/elasticbeanstalk)
</b></details>

<details>
<summary>What is AWS SWF?</summary><br><b>

Amazon definition: "Amazon SWF helps developers build, run, and scale background jobs that have parallel or sequential steps. You can think of Amazon SWF as a fully-managed state tracker and task coordinator in the Cloud."

Learn more on Amazon Simple Workflow Service [here](https://aws.amazon.com/swf)
</b></details>

<details>
<summary>What is AWS EMR?</summary><br><b>

AWS definition: "big data platform for processing vast amounts of data using open source tools such as Apache Spark, Apache Hive, Apache HBase, Apache Flink, Apache Hudi, and Presto."

Learn more [here](https://aws.amazon.com/emr)
</b></details>

<details>
<summary>What is AWS Quick Starts?</summary><br><b>

AWS definition: "Quick Starts are built by AWS solutions architects and partners to help you deploy popular technologies on AWS, based on AWS best practices for security and high availability."

Read more [here](https://aws.amazon.com/quickstart)
</b></details>

<details>
<summary>What is the Trusted Advisor?</summary><br><b>
</b></details>

<details>
<summary>What is AWS Service Catalog?</summary><br><b>

Amazon definition: "AWS Service Catalog allows organizations to create and manage catalogs of IT services that are approved for use on AWS."

Learn more [here](https://aws.amazon.com/servicecatalog)
</b></details>

<details>
<summary>What is AWS CAF?</summary><br><b>

Amazon definition: "AWS Professional Services created the AWS Cloud Adoption Framework (AWS CAF) to help organizations design and travel an accelerated path to successful cloud adoption. "

Learn more [here](https://aws.amazon.com/professional-services/CAF)
</b></details>

<details>
<summary>What is AWS Cloud9?</summary><br><b>

AWS: "AWS Cloud9 is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser"
</b></details>

<details>
<summary>What is AWS CloudShell?</summary><br><b>

AWS: "AWS CloudShell is a browser-based shell that makes it easy to securely manage, explore, and interact with your AWS resources."
</b></details>

<details>
<summary>What is AWS Application Discovery Service?</summary><br><b>

Amazon definition: "AWS Application Discovery Service helps enterprise customers plan migration projects by gathering information about their on-premises data centers."

Learn more [here](https://aws.amazon.com/application-discovery)
</b></details>

<details>
<summary>What is the AWS well-architected framework and what pillars it's based on?</summary><br><b>

AWS definition: "The Well-Architected Framework has been developed to help cloud architects build secure, high-performing, resilient, and efficient infrastructure for their applications. Based on five pillars — operational excellence, security, reliability, performance efficiency, and cost optimization"

Learn more [here](https://aws.amazon.com/architecture/well-architected)
</b></details>

<details>
<summary>What AWS services are serverless (or have the option to be serverless)?</summary><br><b>

AWS Lambda
AWS Athena
</b></details>

<details>
<summary>What is Simple Queue Service (SQS)?</summary><br><b>

AWS definition: "Amazon Simple Queue Service (SQS) is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications".

Learn more about it [here](https://aws.amazon.com/sqs)
</b></details>
