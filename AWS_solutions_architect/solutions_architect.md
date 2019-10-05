## AWS Solutions Architect Associate

##### Exam Blueprint

- 130 minutes in length
- 60~ questions 
- Multiple Choice
- Results are between 100-1000 with a passing score of 720
- Qualification is valid for 2 years
- Scenario based questions

---

### Overview of AWS

---

#### The History of AWS

- Why is AWS so powerful? 
  - Amazon allows companies to use Amazon's Web Servers(AWS) without risks associated with having to build home-grown servers. This allows for companies with tighter budgets to build into AWS and leverage all the integrated server scalability features that Amazon provides. Additionally, it reduces risks to the company because they no longer have to manage and maintain their own server farm.

- In 2003, Chris Pinkham and Benjamin Black presented a paper on what Amazons internal infrastructure could look like. They suggested selling it as a service and prepared a business case for it. 

- SQS was launched in 2004, the very first service released by AWS.

- AWS was a business launched in 2006, targeting developers in Silicon Valley.

- By 2007, AWS had over 180,000 developers on the platform. 

- By 2010, all of amazon.com moved over to the AWS service.

- 2012, first re:Invent conference

- 2013, certifications released 

- 2018, AWS launched Machine Learning Certificates

- 2019, Alexa Specialty Beta certification launched. 

#### AWS Platform 

- **AWS Global Infrastructure** - Amazon's global infrastructure and servers around the world. As of 2019 there are 24 regions and 72 availability zones.

- **Availability Zone** - An AZ is a data center, or cluster of data centers, that are comprised of many servers that support the AWS cloud. In many cases, there are several geographically isolated data centers that protect the network from issues that may knock any one specific center out. 

- **Regions** - A geographical area that consists of 2 or more availability zones.

- **Edge Location** - Edge locations are endpoints for AWS which are used for caching content. Caches files and content from distant regions and holds them in a closer edge location facility.

- **Amazon VPC** - Amazon Virtual Private Cloud, which is part of Networking services is a virtual network dedicated to a single AWS account. It is isolated from other virtual networks in the AWS cloud, providing compute resources with robust and secure networking functionality. 

#### Content to focus on for certification

- Security, Identity, and Compliance
- Network & Content Delivery
- Compute
- Storage
- Databases

#### Keywords: 
 - **Amazon VPC** - Amazon Virtual Private Cloud
 - **Amazon AX** - Availability Zone

#### Questions:
 - **What is a region, an availability zone, and an edge location?**
 - **Where is CloudFront data cached?**

### Identity Access Management & S3

---

### Identity Access Management (IAM) 101

- **Identity Access Management**, IAM allows you to manage users and their level of access to the AWS console. It is important to know for administrating a company's AWS account. Allows you to create users, groups, roles, etc. on the platform and provide permissions. 

##### IAM Features

- Centralized control of you AWS account
- Shared access to you AWS account
- Granular permissions
- Identity federations, allows end-users to potentially log in using their Facebook account, LinkedIn, etc.
- Multi-factor Authentication
- Provide temporary access for users/devices and services
- Allows password rotation policy 
- Integrated with many different AWS services
- Supports PCI DSS Compliance, a compliance required for handling user data and money.

##### IAM Permissions

- **Users** - End Users such as employees
- **Groups** - A collection of users, each user will inherit the permissions of the group.
- **Policies** - Policies are made up of documents called Policy documents. These documents are in JSON (JavaScript Object Notation) format and give permission to what a User/Group/Role is able to do.
- **Roles** - You create roles and assign them to AWS resources. The resources then can communicate with other AWS services.

##### Hands On

- Policy example (AdministratorAccess)

```
// Allow the user to have access to all (*) actions on all (*) resources
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "*",
            "Resource": "*"
        }
    ]
}
```

##### Keywords:

- **IAM** - Identity Access Management
- **Root Account** - Account created when we first setup AWS account. It has complete Admin access.
- **2FA** - Two-factor authentication
- **MFA** - Multi-factor authentication
- **Billing Alarm** - An billing limit you set that will trigger once its been reached. 
- **SNS** - Simple notification service
- **Users**
- **Groups**
- **Policies**
- **Roles**

##### Exam Tips:

- **IAM is universal.** It does not apply to regions at this time.
- The **"root account"** is simply the account created when first setup your AWS account. It has complete Admin access.
- New Users have **NO permissions** when first created.
- New Users are assigned **Access Key ID** & **Secret Access Keys** when first created.
- **These are not the same as a password.** You cannot use the Access key ID & Secret Access Key to Login to the console. You can use this to access AWS via the APIs and Command Line, however.
- **You only get to view these once.** If you lose them, you have to regenerate them. So, save them in a secure location.
- Always set up **Multi-factor Authentication** on your root account.
- You can create and customize your own **password rotation policies.**

##### Exam Scenarios:

- **You need to protect your account from being over-billed. How can you accomplish this?**
  - You go into CloudWatch and you create a billing alarm. A billing alarm uses an SNS topic to email you when your account goes over the specificated threshold.

--- 

### S3 101

---

  - **Simple Storage Service.** One of the oldest services on AWS. It provides developers and IT teams with secure, durable, and highly-scalable object storage. S3 is easy to use with a simple web service interface that allows you to store and retrieve information from anywhere in the world.

#### S3 Features

  - S3 is **Object-based**, ie allows you to upload files
  - Files can range between 0 Bytes to 5 Terabytes
  - There is unlimited storage
  - Files are stored in Buckets (directory). Must have a unique name.
  - S3 is a universal name space. Names must be unique globally.
  - When you upload a file to S3 you will receive an HTTP 200 code.
  - Tiered Storage
  - Life-cycle Management. Allows files to be moved around.
  - Versioning
  - Encryption
  - MFA Delete
  - Secure data using **Access Control Lists** and **Bucket Policies**

#### S3 Objects

  - **Key** - Name of the object
  - **Value** - Data in the form of bytes
  - **Version ID** - Important for versioning
  - **Metadata** - Data about the data
  - **Sub-resources** - Access Control Lists, Torrent

#### How does data consistency work for S3?

  - Read after write for POSTs of new objects. As soon as you upload a file, you can read it.
  - Eventual consistency for overwrite PUTs and DELETEs, if you wait a few moments you will be able to read the latest version.

#### S3 Guarantees

  - 99.99% availability guaranteed by Amazon and 99.99999999999% durability. (Remember 11 x 9's)

#### S3 Storage Classes / Tiers

  - **S3 Standard** - 99.99% availability and 99.99999999999% durability. Data is stored redundantly across multiple devices in multiple facilities and is designed to sustain the loss of 2 facilities concurrently. (Milliseconds to access data)
  - **S3 - IA** - Infrequently Accessed. For less frequently accessed data, but requires rapid access when needed. Lower fee than S3 standard, but you are charged a retrieval fee. (Milliseconds to access data)
  - **S3 One Zone - IA** - Infrequently Accessed. A much cheaper IA option but lacks the multiple AZ data resilience. (Milliseconds to access data)
  - **S3 Intelligent Tiering** - Leverages machine learning to automatically move data to most cost-effective access tier, without performance impact or operational overhead. (Milliseconds to access data)
  - **S3 Glacier** - Secure, durable, low-cost storage class for data archiving. You can reliably store any amount of data at costs that are cheaper than on-premises solutions. Retrieval times are configurable, can range from minutes to hours. (Select minutes or hours to access data)
  - **S3 Glacier Deep Archive** - Amazon S3's lowest-cost storage class. Retrieval time byte latency of 12 hours is acceptable. (Select hours to access data)

#### S3 Charges for:

  - **Storage** 
  - **Requests**
  - **Storage Management Pricing** 
  - **Data Transfer Pricing**
  - **Transfer Acceleration** - Allows for fast, easy, and secure transfers of files over long distances between your end users and an S3 bucket. Transfer Acceleration takes advantage of Amazon CloudFront's globally distributed edge locations. As the data arrives at an edge location, data is then re-routed to Amazon S3 over an optimized network / Amazon's backbone network.
  - **Cross Region Replication** - Allows for data to be automatically replicated in another region. Allows for increased availability and provides disaster durability.

#### S3 Security and Encryption:
  - By default, all newly created buckets are **private**. You can setup access control to your buckets using **Bucket Policies, Access Control Lists**. Additionally, S3 buckets can be configured to create access logs, which cause all requests to be logged and sent to an S3 Bucket on the same account or even on another account.

##### Encryption

  - **Encryption in transit** - HTTPS is an example of encryption in transit. Achieved by **SSL/TLS**.
  - **Encryption at Rest** - Can be handled server-side (amazon helps here), or client-side, where you the developer encrypt the object yourself and upload it to S3. 

##### Server Side Encryption 
  1. **S3 Managed Keys - SSE-S3**, amazon automatically manages the keys (encryption / decryption) for you.
  2. **AWS Key Management Service, Managed Keys - SSE-KMS**, developer and amazon manage the keys together.
  3. **Server Side Encryption with Customer provided keys - SSE-C**, give amazon your own keys, that you manage, and you can use them to encrypt your S3 objects.
  4. **Client side encryption**. Encrypt client side and upload to S3.

#### S3 Version Control

##### Features 

  - Stores all versions of an object, including all writes even if you delete the object.
  - Great back-up tool
  - Once enabled, **versioning cannot be disabled**, only suspended.
  - Integrates with **life-cycle** rules.
  - **Versioning comes with MFA delete capability** which provides another level of security.

#### S3 life-cycle Management and Glacier 

  - Life-cycles allow you to set rules to manage your objects, they can be automated to transition to tiered storage, and eventually they can be automatically set to expire based on retention needs. In short, life-cycles automate the moving of objects between different storage tiers and can be used in conjunction with versioning (can be applied to current and previous versions).

#### Cross Region Replication

  - Allows for data to be automatically replicated in another region. Allows for increased availability and provides disaster durability.
  - Versioning must be enabled on both the source and destination buckets.
  - Regions must be unique.
  - Files in an existing bucket are not replicated automatically.
  - All subsequent updated files will be replicated automatically.
  - Delete markers are not replicated.
  - Deleting individual versions or delete markers will not be replicated.

#### S3 Transfer Acceleration

  - S3 Transfer Acceleration utilizes the **CloudFront Edge Network** to accelerate you uploads to S3. Instead of uploading directly to your S3 bucket, you can use a distinct URL to upload directly to an edge location which will then transfer that file to S3. You will get a distinct URL to upload to.

#### Keywords:

  - **RRS** - Reduced Redundancy Storage

#### Exam Tips:

  - Remember that S3 is **Object Based**: i.e. allows you to upload files. 
  - Files can be from **0 Bytes** to **5 TB**.
  - There is **unlimited storage**.
  - Files are stored in **Buckets**.
  - **S3 is a universal namespace.** That is, names must be unique globally.
  - Not suitable to install an operating system or database on.
  - Successful uploads will generate a **HTTP 200** status code.
  - You can turn on **MFA Delete**
  - Read after Write consistency for **PUTS** of new Objects.
  - **Eventual Consistency** for overwrite PUTS and DELETES (Can take some time to propagate)
  - **STORAGE CLASSES!**
    - S3 Standard
    - S3 - IA
    - S3 One Zone - IA
    - S3 - Intelligent Tiering
    - S3 Glacier
    - S3 Glacier Deep Archive
  - Read the S3 FAQs before taking the exam. It comes up A LOT!
  - Control access to buckets using either a **bucket ACL** or using **Bucket Polices**
  - Versioning stores all versions of an object (including all writes and even if you delete an object)
  - Life Cycle allows your to automate moving your objects between the different storage tiers.

  --- 

### CloudFront

  ---

#### What is CloudFront?

  - A **content delivery network (CDN)** is a system of distributed servers (network) that deliver webpages and other web content to a user based on the geographic locations of the user, the origin of the webpage, and a content delivery server.

##### CloudFront - Key Terminology 

  - **Edge Location** - This is the location where content will be cached. This is separate to an AWS Region/Availability Zone.
  - **Origin** - This is the origin of all the files that the CDN will distribute. This can be an S3 Bucket, an EC2 Instance, an Elastic Load Balancer, or Route53.
  - **Distribution** - This is the name given to the CDN which consists of a collection of Edge Locations.

#### How it works:

  - **Amazon CloudFront** can be used to deliver your entire website, including dynamic, static, streaming, and interactive content using a global network of edge locations. Requests for your content are automatically routed to the nearest edge location, so content is delivered with the best possible performance. 

##### CloudFront - Distributions

  - **Web Distributions** - Typically used for Websites. 
  - **RTMP Distributions** - Used for Media Streaming

##### Invalidations 

  - Invalidating objects removes them from CloudFront edge caches. A faster and less expensive method is to use versioned object or director names. 
  - Exam Scenario:
    - **The correct way to deal with pushing out some data and then you figure out something's wrong and you do update but it's not showing up correctly?** The way to deal with that is to create an Invalidation

#### Exam Tips:

  - **Edge Location** - This is the location where content will be cached. This is separate to an AWS Region / Availability Zone.
  - **Origin** - This is the origin of all the files that the CDN will distribute. This can be either an S3 Bucket, an EC2 Instance, an Elastic Load Balancer, or Route53.
  - **Distribution** - This is the name given to the CDN which consists of a collection of Edge Locations.
  - **Web Distributions** - Typically used for Websites. 
  - **RTMP Distributions** - Used for Media Streaming
  - Edge location are not just **READ** only - you can write to them too. (ie put an object on to them).
  - Objects are cached for the life of the **TTL (Time To Live)**
  - You can clear cached objects, but you will be charged. 

---

### Snowball

---

#### What is Snowball?

  - Snowball is a petabyte-scale data transport solution that uses secure appliances to transfer large amount of data into and out of AWS.
  - Using Snowball address common challenges with **large-scale data transfers** including high network costs, long transfer times, and security concerns. 
  - Transferring data with Snowball is simple, fast, secure, and can be as little as one-fifth the cost of high-speed internet.

##### How it works:

  - Snowball comes in either a **50TB or 80TB size**.
  - Snowball uses multiple layers of security designed to protect your data including **tamper-resistant enclosures, 256-bit encryption, and an industry-standard Trusted Platform Module (TPM)** designed to ensure both security and full chain-of-custody of your data.
  - Once the data transfer job has been processed and verified, AWS performs a software erasure of the Snowball appliance.

#### What is Snowball Edge?

  - AWS Snowball Edge is a **100TB data transfer device** with on-board storage and compute capabilities.
  - You can use Snowball Edge to move large amounts of data into and out of AWS, as a temporary storage tier for large local data-sets, or to support local workloads in remote or offline locations.

##### How it works: 

  - Snowball Edge **connects to your existing applications and infrastructure** using standard storage interfaces, **streamlining the data transfer process and minimizing setup and integration**. 
  - Snowball Edge can **cluster together to form a local storage tier and process your data on-premises**, helping ensure your applications continue to run even when they are not able to access the cloud.

#### What is Snowmobile?

  - AWS Snowmobile is an **Exabyte-scale data transfer service** used to move extremely large amounts of data to AWS.
  - You can transfer up to **100PB per Snowmobile**, a 45-foot long ruggedize chipping container, pulled by a semi-trailer truck. 
  - Snowmobile makes it easy to move massive volumes of data to the cloud, including **video libraries, image repositories, or even a complete data center migration**.
  - Transferring data with Snowmobile is **secure, fast, and cost effective**.

#### When Should I Use Snowball?

| Available Internet Connection  | Theoretical Min. Number of Days to Transfer 100TB at 80% Network Utilization | When to Consider AWS Import/Export Snowball? |
| ------------- | ------------- | ------------- |
| T3 (44.736Mbps) | 269 days | 2TB or more |
| 100Mbps | 120 days | 5TB or more |
| 1000Mbps | 12 days | 60TB or more |

#### Exam Tips: 

  - Understand what Snowball is
  - Snowball can Import to S3
  - Snowball can Export from S3
  - Exam Scenario:
    - **What would you use if you wanted to transfer a large amount of data into the AWS cloud?** You'll want to use Snowball!

---
### Storage Gateway
---

#### What is Storage Gateway?

  - AWS Storage Gateway is a service that connects an on-premises software appliance with cloud-based storage to provide seamless and secure integration between an organization's on-premises IT environment and AWS's storage infrastructure. 
  - The service enables your to securely store data to the AWS cloud for **scalable and cost-effective storage**.

#### How to use Storage Gateway

  - AWS Storage Gateway's software appliance is available for download as a **virtual machine (VM) image** that you install on a host in your data-center. 
  - Storage Gateway supports either VMware ESXi or Microsoft Hyper-V. 
  - Once you've installed your gateway and associated it with your AWS account through the activation process, you can use the AWS Management Console to create the storage gateway option that is right for you.

#### The Three Different Types of Storage Gateway

  - **File Gateway (NFS & SMB)**
  - **Volume Gateway (iSCSI)** - Stored Volumes, Cached Volumes
  - **Tape Gateway (VTL)**

#### File Gateway

  - Files are stored as objects in you S3 buckets, accessed through a **Network File System (NFS)** mount point. 
  - Ownership, permissions, and timestamps are durably stored in S3 in the user-metadata of the object associated with the file. 
  - Once objects are transferred to S3, they can be managed as native S3 objects, and bucket policies such as versioning, life-cycle management, and cross-region replication apply directly to objects stored in your bucket.

#### Volume Gateway

  - The volume interface presents your applications with disk volumes using the **iSCSI block protocol**.
  - Data written to these volumes can be asynchronously backed up as point-in-time snapshots of your volumes, and stored in the cloud as Amazon EBS snapshots.
  - **Snapshots are incremental backups that capture only changed blocks**. All snapshot storage is also compressed to minimize your storage charges.

##### Stored Volumes 

  - Stored volumes let you store your primary data locally, while asynchronously backing up that data to AWS.
  - Stored volumes provide your on-premises applications with low-latency access to their entire data-sets, while providing durable, off-site backups. 
  - You can create storage volumes and mount them ad iSCSI devices from your on-premises application servers. 
  - Data written to your stored volumes is stored on your on-premises storage hardware. This data is asynchronously backed up to Amazon S3 in the form on Amazon Elastic Block Store snapshots. 1GB - 16TB in size for Stored Volumes.

##### Cached Volumes

  - Cached Volumes let you use Amazon S3 as your primary data storage while retaining frequently accessed data locally in your storage gateway.
  - Cached Volumes minimize the need to scale your on-premises storage infrastructure, while still providing your applications with low-latency access to their frequently accessed data. 
  - You can create storage volumes up to 32 TB in size and attach to them as iSCSI devices from your on-premises application servers. 
  - Your gateway stores data that your write to these volumes in Amazon S3 and retains recently read data in your on-premises storage gateway's cache and upload buffer storage. 1GB - 32TB in size for Cached Volumes.

##### Tape Gateway

  - Tape Gateway offers a durable, cost-effective solution to archive your data in the AWS Cloud.
  - The VTL interface it lets you leverage your existing tape-based backup application infrastructure to store data on virtual tap cartridges that you create on your tape gateway.
  - Each tape gateway is pre-configured with a media changer and tape drives, which are available to your existing client backup application as iSCSI devices. 
  - You add tape cartridges as you need to archive your data. Supported by NetBackup, Backup Exec, Veeam etc.

#### Exam Tips:

  - **File Gateway** - For flat files, stored directly on S3. 
  - **Volume Gateway**
    - **Stored Volumes** - Entire data-set is stored on site and is asynchronously backed up to S3.
    - **Cached Volumes** - Entire data set is stored on S3 and the most frequently accessed data is cached on site.
  - **Gateway Virtual Tape Library**

---
### IAM & S3 Summary
---

#### IAM Exam Tips:

  - **Identity Access Management** consists of the following:
    - **Users**
    - **Groups**
    - **Roles**
    - **Policies**
  - **IAM is universal**. It does not apply to regions at this time.
  - The **"root account"** is simply the account created when first setup your AWS account. It has complete Admin access.
  - New Users have **NO permissions** when first created.
  - New Users are assigned **Access Key ID** & **Secret Access Keys** when first created.
  - **These are not the same as a password**. You cannot use the Access Key ID & Secret Access Key to Login to the console. You can use this to access AWS via the API's and Command Line, however.
  - Always setup **Multi-factor Authentication** on your root account.
  - You can create and customize your own **password rotation policies**.

#### S3 Exam Tips:

  - Remember that S3 is **Object-based**: i.e. allows you to upload files.
  - Files can be from **0 Bytes to 5 TB**.
  - There is **unlimited storage**.
  - Files are stored in **Buckets**.
  - **S3 is a universal namespace**. That is, names must be unique globally.
  - Not suitable to install an operating system on.
  - Successful uploads will generate a **HTTP 200** status code.
  - By default, all newly created buckets are **PRIVATE**. You can setup access control to your buckets using:
    - **Bucket Policies**
    - **Access Control Lists**
  - S3 buckets can be configured to create access logs which log all requests made to the S3 bucket. This can be sent to another bucket and even another bucket in another account.
  - The Key Fundamentals of S3 are:
    - **Key** (This is simply the name of the object)
    - **Value** (This is simply the data and is made up of a sequence of bytes)
    - **Version ID** (Important for Versioning)
    - **Metadata** (Data about data you are storing)
    - **Sub-resources**
      - Access Control Lists
      - Torrent
  - Read after Write consistency for PUTS of new Objects
  - Eventual Consistency for overwrite PUTS and DELETES (can take some time to propagate)
  - **S3 STORAGE TIERS!**
     - **S3 Standard** - 99.99% availability and 99.99999999999% durability. Data is stored redundantly across multiple devices in multiple facilities and is designed to sustain the loss of 2 facilities concurrently. (Milliseconds to access data)
    - **S3 - IA** - Infrequently Accessed. For less frequently accessed data, but requires rapid access when needed. Lower fee than S3 standard, but you are charged a retrieval fee. (Milliseconds to access data)
    - **S3 One Zone - IA** - Infrequently Accessed. A much cheaper IA option but lacks the multiple AZ data resilience. (Milliseconds to access data)
    - **S3 Intelligent Tiering** - Leverages machine learning to automatically move data to most cost-effective access tier, without performance impact or operational overhead. (Milliseconds to access data)
    - **S3 Glacier** - Secure, durable, low-cost storage class for data archiving. You can reliably store any amount of data at costs that are cheaper than on-premises solutions. Retrieval times are configurable, can range from minutes to hours. (Select minutes or hours to access data)
    - **S3 Glacier Deep Archive** - Amazon S3's lowest-cost storage class. Retrieval time byte latency of 12 hours is acceptable. (Select hours to access data)
  - Encryption In Transit is achieved by:
    - **SSL/TLS**
  - Encryption At Rest (Server Side) is achieved by:
    - **S3 Managed Keys - SSE-S3**
    - **AWS Key Management Service, Managed Keys - SSE-KMS**
    - **Server Side Encryption With Customer Provided Keys - SSE-C**

#### Cross Region Replication

  - Allows for data to be automatically replicated in another region. Allows for increased availability and provides disaster durability.
  - **Versioning must be enabled** on both the source and destination buckets.
  - Regions must be **unique**.
  - Files in an existing bucket are **not replicated automatically**.
  - All subsequent updated files will be **replicated automatically**.
  - Delete markers are not replicated.
  - Deleting individual versions or delete markers will not be replicated.

#### Life Cycle Policies

  - Automates moving your objects between the different storage tiers.
  - Can be used in conjunction with versioning.
  - Can be applied to current versions and previous versions.

#### S3 Transfer Acceleration

  - Instead of uploading directly to your S3 bucket, you can use a distinct URL to upload directly to an edge location which will then transfer that file to S3.

#### CloudFront

  - **Edge Location** - This is the location where content will be cached. This is separate to an AWS Region / Availability Zone.
  - **Origin** - This is the origin of all the files that the CDN will distribute. This can be either an S3 Bucket, an EC2 Instance, an Elastic Load Balancer, or Route53.
  - **Distribution** - This is the name given to the CDN which consists of a collection of Edge Locations.
    - **Web Distribution** - Typically used for Websites.
    - **RTMP** - Used for Media Streaming.
  - Edge locations are not just **READ** only -- you can **write** to them too! (i.e. put an object on to them)

#### Snowball

  - Understand what Snowball is
  - Snowball can **Import to S3** 
  - Snowball can **Export from S3** 

#### Storage Gateway

  - **File Gateway**
    - For flat files, stored directly on S3.
  - **Volume Gateway**
    - **Stored Volumes** - Entire data-set is stored on site and is asynchronously backed up to s3.
    - **Cached Volumes** - Entire data-set is stored on S3 and the most frequently accessed data is cached on site.
  - **Gateway Virtual Tape Library**
    - Used for backup and uses popular backup applications like NetBackup, Backup Exec, Veeam etc.

---
### Identity Access Management & S3 Quiz
---

- What is an additional way to secure the AWS accounts of both the root account and new users alike?
  - Implement Multi-Factor Authentication for all accounts.
- Which of the following is not a component of IAM?
  - Organizational Units
- When you create a new user, that user ________.
  - Will be able to interact with AWS using their access key ID and secret access key using the API, CLI, or the AWS SDKs
- Which statement best describes IAM?
  - IAM allows you to manage users, groups, roles, and their corresponding level of access to the AWS Platform.
- Using SAML (Security Assertion Markup Language 2.0), you can give your federated users single sign-on (SSO) access to the AWS Management Console.
  - TRUE
- In what language are policy documents written?
  - JSON
What is the default level of access a newly created IAM User is granted?
  - No access to any AWS services
- Which of the following is not a feature of IAM?
  - IAM allows you to set up biometric authentication, so that no passwords are required.
- You have a client who is considering a move to AWS. In establishing a new account, what is the first thing the company should do?
  - Set up an account using their company email address.
- A new employee has just started work, and it is your job to give her administrator access to the AWS console. You have given her a user name, an access key ID, a secret access key, and you have generated a password for her. She is now able to log in to the AWS console, but she is unable to interact with any AWS services. What should you do next?
  - Grant her Administrator access by adding her to the Administrators' group.
- What level of access does the "root" account have?
  - Administrator Access
- Power User Access allows ________.
  - Access to all AWS services except the management of groups and users within IAM.
- You are a solutions architect working for a large engineering company that are moving from a legacy infrastructure to AWS. You have configured the company's first AWS account and you have set up IAM. Your company is based in Andorra, but there will be a small subsidiary operating out of South Korea, so that office will need its own AWS environment. Which of the following statements is true?
  - You will need to configure Users and Policy Documents only once, as these are applied globally.
- You are a security administrator working for a hotel chain. You have a new member of staff who has started as a systems administrator, and she will need full access to the AWS console. You have created the user account and generated the access key id and the secret access key. You have moved this user into the group where the other administrators are, and you have provided the new user with their secret access key and their access key id. However, when she tries to log in to the AWS console, she cannot. Why might that be?
  - You cannot log in to the AWS console using the Access Key ID / Secret Access Key pair.
- Every user you create in the IAM systems starts with ________.
  - No Permissions
- A __________ is a document that provides a formal statement of one or more permissions.
  - Policy
- You have created a new AWS account for your company, and you have also configured multi-factor authentication on the root account. You are about to create your new users. What strategy should you consider in order to ensure that there is good security on this account.
  - Enact a strong password policy.
- You have been asked to advise on a scaling concern. The client has an elegant solution that works well. As the information base grows they use CloudFormation to spin up another stack made up of an S3 bucket and supporting compute instances. The trigger for creating a new stack is when the PUT rate approaches 100 PUTs per second. The problem is that as the business grows that number of buckets is growing into the hundreds and will soon be in the thousands. You have been asked what can be done to reduce the number of buckets without changing the basic architecture.
  - Change the trigger level to around 3000 as S3 can now accommodate much higher PUT and GET levels.
- You run a meme creation website where users can create memes and then download them for use on their own sites. The original images are stored in S3 and each meme's metadata in DynamoDB. You need to decide upon a low-cost storage option for the memes, themselves. If a meme object is unavailable or lost, a Lambda function will automatically recreate it using the original file from S3 and the metadata from DynamoDB. Which storage solution should you use to store the non-critical, easily reproducible memes in the most cost-effective way?
  - S3 - 1Zone-IA
- You have uploaded a file to S3. Which HTTP code would indicate that the upload was successful?
  - HTTP 200
- S3 has eventual consistency for which HTTP Methods?
  - Overwrite PUTS and DELETES
- What is Amazon Glacier?
  - An AWS service designed for long term data archival.
- You work for a health insurance company that amasses a large number of patients' health records. Each record will be used once when assessing a customer, and will then need to be securely stored for a period of 7 years. In some rare cases, you may need to retrieve this data within 24 hours of a claim being lodged. Given these requirements, which type of AWS storage would deliver the least expensive solution?
  - Glacier
- The difference between S3 and EBS is that EBS is object-based whereas S3 is block-based.
  - FALSE
- What is the availability of S3 – OneZone-IA?
  - 99.50%
- One of your users is trying to upload a 7.5GB file to S3. However, they keep getting the following error message: "Your proposed upload exceeds the maximum allowed object size.". What solution to this problem does AWS recommend?
  - Design your application to use the Multipart Upload API for all objects.
- You run a popular photo-sharing website that depends on S3 to store content. Paid advertising is your primary source of revenue. However, you have discovered that other websites are linking directly to the images in your buckets, not to the HTML pages that serve the content. This means that people are not seeing the paid advertising, and you are paying AWS unnecessarily to serve content directly from S3. How might you resolve this issue?
  - Remove the ability for images to be served publicly to the site and then use signed URLs with expiry dates.
- You have been asked by your company to create an S3 bucket with the name "acloudguru1234" in the EU West region. What would the URL for this bucket be?
  - https://s3-eu-west-1.amazonaws.com/acloudguru1234
- You work for a major news network in Europe. They have just released a new mobile app that allows users to post their photos of newsworthy events in real-time, which are then reviewed by your editors before being copied to your website and made public. Your organization expects this app to grow very quickly, essentially doubling its user base each month. The app uses S3 to store the images, and you are expecting sudden and sizable increases in traffic to S3 when a major news event takes place (as users will be uploading large amounts of content.) You need to keep your storage costs to a minimum, and it does not matter if some objects are lost. With these factors in mind, which storage media should you use to keep costs as low as possible?
  - S3 - One Zone-Infrequent Access
- How many S3 buckets can I have per account by default?
  - 100
- You work for a busy digital marketing company who currently store their data on-premise. They are looking to migrate to AWS S3 and to store their data in buckets. Each bucket will be named after their individual customers, followed by a random series of letters and numbers. Once written to S3 the data is rarely changed, as it has already been sent to the end customer for them to use as they see fit. However, on some occasions, customers may need certain files updated quickly, and this may be for work that has been done months or even years ago. You would need to be able to access this data immediately to make changes in that case, but you must also keep your storage costs extremely low. The data is not easily reproducible if lost. Which S3 storage class should you choose to minimize costs and to maximize retrieval times?
  - S3 - IA
- What is the availability of objects stored in S3?
  - 99.99%
- S3 has what consistency model for PUTS of new objects?
  - Read After Write Consistency
- What does S3 stand for?
  - Simple Storage Service
- You are a solutions architect who works with a large digital media company. The company has decided that they want to operate within the Japanese region and they need a bucket called "testbucket" set up immediately to test their web application on. You log in to the AWS console and try to create this bucket in the Japanese region however you are told that the bucket name is already taken. What should you do to resolve this?
  - Bucket names are global, not regional. This bucket name is already taken. You should choose another bucket name.
- What is the minimum file size that I can store on S3?
  - 0 Bytes
- What is AWS Storage Gateway?
  - It is a physical or virtual appliance that can be used to cache S3 locally at a customer's site.

---
### Elastic Compute Cloud, EC2 
---

### EC2 101

  - **Elastic Compute Cloud**, Amazon EC2 is a web service that provides resizable compute capacity in the cloud.
  - Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, this provides for the ability to quickly scale capacity both up and down as your computing requirements change.
  - The EC2 solution is drastically faster than traditional server solutions where setting up and deploying physical servers could take days or even months and the costs would all be upfront. 
  - EC2 allows for provisioning servers in the cloud and takes mere minutes to complete.

#### Pricing Models Instances

  - **On Demand** - No commitment model that allows you to pay by the hour or even second.
  - **Reserved** - Provides a capacity reservation and offers a significant discount on the hourly charge for an instance. **Contact terms are 1 or 3 year terms**.
  - **Spot** - Enables you to bid on excess EC2 capacity. Amazon will drop the price on EC2 instances to encourage people to use that surplu capacity. You would set price you're willing to bid at and when the prices for the EC2 instances lowers you will have access to those additional resources. As the on-demand demand goes up, the prices for those instances will go up and if they pass your price point you will lose access to them until the next occurrence of reduced prices. It's essentially a market for buying into extra resources when they're in supply. 
  - **Dedicated Host** - Physical EC2 server dedicated for your use. Dedicated hosts can help you reduce costs by allowing you to use your existing server-bound software licenses.
  
##### On Demand Pricing

> Ideal for:
  
  - Users that want low cost and flexibility of EC2 without any upfront payment or long-term commitment.
  - Applications with short term, spiky, or unpredictable workloads that cannot be interrupted.
  - Applications being developed or tested on Amazon EC2 for the first time.

##### Reserved Pricing

> Ideal for: 

  - Applications with steady state or predictable usage.
  - Applications that require reserved capacity.
  - Users are able to make upfront payments to reduce their total computing cost even further.

##### 3 Types:

  - **Standard Reserved Instances** - Offer up to 75% off on-demand instances. The more you pay upfront and the longer the contract the greater the discount.
  - **Convertible Reserved Instances** - Offer up to 54% off on-demand instances and allow you to change from one reserved **EC2 Instance Type** to another.
  - **Scheduled Reserved Instances** - Available to launch within the time windows you reserve. This option allows you to match you capacity reservation along a predictable recurring schedule.

##### Spot Pricing

> Ideal for:

  - Applications that have flexible start and end times.
  - Applications that are only feasible at very low compute prices.
  - Users with urgent computing needs for large amounts of additional capacity.
  - If your spot instance is terminated by EC2, you will not be charged for partial hour usage. If you terminate the instance yourself, you will be charged for any hour which the instance ran.

##### Dedicated Host Pricing 

> Ideal for:

  - Useful for regulatory requirements that may not support multi-tenant virtualization.
  - Great for licensing which does not support multi-tenancy or cloud deployments (like Oracle licensing).
  - Can be purchased on-demand.
  - Can be purchased ad a Reservation for up to 70% off the on-demand price.

#### Exam Tips: 

  - Remember what Amazon EC2 is:
    - **Elastic Compute Cloud**, Amazon EC2 is a web service that provides resizable compute capacity in the cloud. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, this provides for the ability to quickly scale capacity both up and down as your computing requirements change.
  - Pricing Models Instances
    - **On Demand**
    - **Reserved**
    - **Spot**
    - **Dedicated Host**
  - If the Spot instance is terminated by Amazon EC2, you will not be charged for a partial hour of usage. However, if you terminate the instance yourself, you will be charged for any hour in which the instance ran.

--- 
### Launch Our First EC2 Instance
---

#### Exam Tips:

  - Termination Protection is **turned off** by default, you must turn it on.
  - On an EBS-backed instance, the **default action is for the root EBS volume to be deleted** when the instance is terminated.
  - EBS Root Volumes of your DEFAULT AMI's cannot be encrypted. You can also use a third party tool (such as bit locker etc.) to encrypt the root volume, or this can be done when creating AMI's in the AWS console or using the API.

--- 
### Security Groups Basics
---

  - Every time you make a rule change in a security group, that change takes affect immediately. If you delete your inbound HTTP port 80 rules you will immediately lose the ability to access the website.
  - **Security Groups are stateful**, when you create an inbound rule an outbound rule is created automatically. If you allow HTTP, SSH, etc. in,it is automatically allowed back out.
  - Security groups work by blocking everything by default, you as the developer have to allow traffic like HTTP, mySQL, etc. to go through.
  - All inbound traffic is blocked by default.
  - All outbound traffic is allowed.
  - Changes to security groups take effect immediately.
  - You can have multiple security groups attached to EC2 Instances.
  - You can specify allow rules, but not deny rules.

#### Exam Tips: 

  - All inbound traffic is blocked by default.
  - All outbound traffic is allowed.
  - Changes to security groups take effect immediately.
  - You can have any number of EC2 instances within a security group.
  - You can have multiple security groups attached to EC2 Instances.
  - Security Groups are **STATEFUL**
  - If you create an inbound rule allowing traffic in, that traffic is automatically allowed back out again.
  - You cannot block specific IP addresses using Security Groups, instead use Network Access Control Lists.
  - You can specify allow rules, but not deny rules.