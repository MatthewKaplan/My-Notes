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

---
### EBS 101
---

  - **Elastic Block Store**, it provides persistent block storage volumes for use with Amazon EC2 instances in the AWS cloud. **Each Amazon EBS volume is automatically replicated within its Availability Zone to protect you from component failure**, offering high availability and durability. In short, EBS is virtual HDD in the cloud.

#### 5 Types of EBS Storage

> gp2, io1, st1, sc1, standard

- **General Purpose (SSD)** - **gp2** - Balance of price and performance suitable for most workloads.
  > _Volume Size: 1 GiB - 16 TiB, Max IOPS Volume: 16,000_
- **Provisioned IOPS (SSD)** - **io1** - Highest Performance SSD volume designed for mission-critical applications.
  > _Volume Size: 4 GiB - 16 TiB, Max IOPS Volume: 64,000_
- **Throughput Optimized HDD** - **st1** - Lost cost HDD volume suitable for Big Data & Data Warehouses
  > _Volume Size: 500 GiB - 16 TiB, Max IOPS Volume: 500_
- **Cold HDD** - **sc1** - File Servers
  > _Volume Size: 500 GiB - 16 TiB, Max IOPS Volume: 250_
- **EBS magnetic HDD** - **standard** - Workloads where data is infrequently accessed and not using something like S3 Glacier.
  > _Volume Size: 1 GiB - 1 TiB, Max IOPS Volume: 40-200_

---
### Volumes and Snapshots
---

- Volumes exist on EBS. Think of EBS as a virtual hard disk.
- **Snapshots exist on S3**. Think of snapshots as a photograph of the disk.
- Snapshots are point-of-time copies of Volumes.
- **Snapshots are incremental** -- this means that only the blocks that have changed since your last snapshot are moved to S3.
- The first snapshot takes some time to create.
- To create a snapshot for Amazon EBS volumes that serve as root devices, you should stop the instance before taking the snapshot to ensure it is consistent. Though, it can still be taken while the instance is running.
- You can create AMI's from both Volumes and Snapshots.
- You can change EBS volume sizes on the fly, including changing the size and storage type.
- Volumes will **ALWAYS** be in the AZ as the EC2 instance.
- EC2 AZ change. EC2 volumes can be moved from one AZ to another. To move an EC2 volume, take a snapshot of it, create an AMI from the snapshot, then use the AMI to launch the EC2 instance in a new AZ.
- EC2 Region change. Take a snapshot of the EC2 volume, create an AMI from the snapshot, copy the AMI from one region to another. Then use the copied AMI to launch the new EC2 instance in the new region.

* **What ever AZ an EC2 instance is located, the EBS volume with be in the same location.** When you have a virtual machine, you would want the virtual hard drive to be as close as possible, so having them in the same location is a logical conclusion.

* **How do you move an EDS volume to a new location?**

* a **snapshot** is a "photograph" of the disk.

* **When you terminate an EC2 instance will the root and EBS volumes all terminate?**
  _No. When you terminate an EC2 instance only the root volume will terminate with it. You will need to manually terminate additional EBS volumes that you had provisioned._

---
### AMI Types (EBS vs Instance Store)
--- 

#### You can select your AMI based on:

  - Region (see Regions and Availability Zones)
  - Operating system
  - Architecture
  - Launch Permissions
  - Storage for the Root Device (Root Device Volume)
    - Instance Store (**EPHEMERAL STORAGE**)
    - EBS Backed Volumes

#### Exam Tips: 

  - Instance Store Volumes are sometimes called **Ephemeral Storage**.
  - Instance store volumes cannot be stopped. If the underlying host fails, you will lose your data.
  - EBS backed instances can be stopped. You will not lose the data on this instance if it is stopped.
  - You can reboot both, you will not lose your data. 
  - By default, both ROOT volumes will be deleted on termination. However, with EBS columns, you can tell AWS to keep the root device volume.

---
### Encrypted Root Device Volumes & Snapshots
---

#### Exam Tips: 

  - Snapshots of encrypted volumes are encrypted automatically.
  - Volumes restored from encrypted snapshots are encrypted automatically.
  - You can share snapshots, but only if they are un-encrypted.
  - These snapshots can be shared with other AWS accounts or made public.
  - You can now encrypt root device volumes upon creation of the EC2 instance.
  - Create a Snapshot of the un-encrypted root device volume.
  - Create a copy of the Snapshot and select the encrypt option.
  - Create an AMI from the encrypted Snapshot.
  - Use that AMI to launch new encrypted instances.

---
### CloudWatch
---

  - **Amazon CloudWatch** is a monitoring service to monitoring service to monitor you AWS resources, as well as the applications that you run on AWS.

#### CloudWatch can monitor things like:

  - Compute
    - EC2 Instances
    - Autoscaling Groups 
    - Elastic Load Balancers
    - Route53 Health Checks
  - Storage & Content Delivery
    - EBS Volumes 
    - Storage Gateways
    - CloudFront

##### Host Level Metrics Consist of:

  - CPU
  - Network
  - Disk
  - Status Check

#### What is AWS CloudTrail?

  - **AWS CloudTrail** increases visibility into your user and resource activity by recording AWS Management Console actions and API calls. 
  - You can identify which users and accounts called AWS, the source IP address from which the calls were made, and when the calls occurred.

##### CloudTrail vs CloudWatch

  - **CloudWatch** monitors performance.
  - **CloudTrail** monitors API calls in the AWS platform.

#### Exam Tips: 

  - CloudWatch is used for monitoring performance.
  - CloudWatch can monitor most of AWS as well as your applications that run on AWS.
  - CloudWatch with EC2 will monitor events every 5 minutes by default.
  - You can have 1 minute intervals by turning on detailed monitoring.
  - You can create CloudWatch alarms which trigger notifications.
  - CloudWatch is all about performance. CloudTrail is all about auditing.
  - Standard Monitoring = 5 Minutes
  - Detailed Monitoring = 1 Minute
  - **What Can I do With CloudWatch?**
    - **Dashboards** - Creates awesome dashboards to see what is happening with your AWS environment.
    - **Alarms** - Allows you to set Alarms that notify you when particular thresholds are hit.
    - **Events** - CloudWatch Events helps you to respond to state changes in your AWS resources.
    - **Logs** - CloudWatch Logs helps you to aggregate, monitor, and store logs.

--- 
### AWS Command Line
--- 

#### Exam Tips:

  - You can interact with AWS from anywhere in the world just by using the command line (CLI)
  - You will need to set up access in **IAM**
  - Commands themselves are not in the exam, but some basic commands will be useful to know for real life.

--- 
### Using IAM Roles With EC2
---

#### Exam Tips: 

  - Roles are more secure than storing your access key and secret access key on individual EC2 instances.
  - Roles are easier to manage.
  - Roles can be assigned to an EC2 instance after it is created using both the console & command line.
  - Roles are universal -- you can use them in any region.

---
### EC2 Instance Meta Data
---

#### Exam Tips: 

  - Used to get information about an instance (such as public ip)
  - curl http://169.254.169.254/latest/meta-data/
  - curl http://169.254.169.254/latest/user-data/

---
### Elastic File System
---

  - **Amazon Elastic File System (Amazon EFS)** is a file storage service for Amazon Elastic Compute Cloud (Amazon EC2) instances.
  - Amazon EFS is easy to use and provides a simple interface that allows you to create and configure file systems quickly and easily.
  - With Amazon EFS, storage capacity is elastic, growing and shrinking automatically as you add and remove files, so your applications have the storage they need, when they need it.

#### Exam Tips: 

  - Supports the Network File System version 4 (NFSv4) protocol.
  - You only pay for the storage you use (no pre-provisioning required).
  - Can scale up to the petabytes.
  - Can support thousands of concurrent NFS connections.
  - Data is stored across multiple Availability Zones within a region.
  - Read After Write Consistency.

---
### EC2 Placement Groups
---

#### Three Types of Placement Groups

  - **Clustered Placement Group**
  - **Spread Placement Group**
  - **Partitioned**

##### Clustered Placement Group

  - A **cluster placement group** is a grouping of instancs within a single Availability Zone. Placement groups are recommended for applications that need low network latency, high network thoughput, or both.

  - Only certain instances can be launched in to a Clustered Placement Group.

##### Spread Placement Group

  - a **Spread Placement Group** is a group of instances that are each placed on distinct underlying hardware.

  - Spread placement groups are recommended for applications that have a small number of critical instances that should be kept separate from each other.

  - THINK INDIVIDUAL INSTANCES

##### Partitioned Placement Group

  - When using **Partitioned Placement Groups**, Amazon EC2 divides each group into logical segments called partitions. Amazon EC2 ensures that each partition within a placement group has its own set of racks. Each rack has its own network and power source. No two partitions within a placement group share the same racks, allowing you to isolate the impact of hardware failure within your application.

  - THINK MULTIPLE INSTANCES

#### Exam Tips: 

  - Three Types of Placement Groups
    - **Clustered Placement Group**
      - Low Network Latency / High Network Throughput
    - **Spread Placement Group**
      - Individual Critical EC2 instances
    - **Partitioned**
      - Multiple EC2 instances HDFS, HBase, and Cassandra
  - A clustered placement group can't span multiple Availability Zones.
  - A spread placement and partitioned group can.
  - The name you specify for a placement group must be unique within your AWS account.
  - Only certain types of instances can be launched in a placement group (Compute Optimized, GPU, Memory Optimized, Storage Optimized)
  - AWS recommend homogenous instances within clustered placement groups.
  - You can't merge placement groups.
  - You can't move an existing instance into a placement group. You can create an AMI from your existing instance, and then launch a new instance from the AMI into a placement group.

---
### EC2 Summary
---

### EC2

  - **What is EC2?**
    - **Elastic Compute Cloud**, Amazon EC2 is a web service that provides resizable compute capacity in the cloud. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, this provides for the ability to quickly scale capacity both up and down as your computing requirements change.
  - **EC2 Pricing options**
    - **On Demand** - No commitment model that allows you to pay by the hour or even second.
    - **Reserved** - Provides a capacity reservation and offers a significant discount on the hourly charge for an instance. **Contact terms are 1 or 3 year terms**.
    - **Spot** - Enables you to bid on excess EC2 capacity. Amazon will drop the price on EC2 instances to encourage people to use that surplu capacity. You would set price you're willing to bid at and when the prices for the EC2 instances lowers you will have access to those additional resources. As the on-demand demand goes up, the prices for those instances will go up and if they pass your price point you will lose access to them until the next occurrence of reduced prices. It's essentially a market for buying into extra resources when they're in supply. 
    - **Dedicated Host** - Physical EC2 server dedicated for your use. Dedicated hosts can help you reduce costs by allowing you to use your existing server-bound software licenses.
  - If the Spot instance is terminated by Amazon EC2, you will not be charged for a partial hour of usage. However, if you terminate the instance yourself, you will be charged for any hour in which the instance ran.

### EBS

  - Termination Protection is **turned off** by default, you must turn it on.
  - On an EBS-backed instance, the **default action is for the root EBS volume to be deleted** when the instance is terminated.
  - EBS Root Volumes of your DEFAULT AMI's cannot be encrypted. You can also use a third party tool (such as bit locker etc.) to encrypt the root volume, or this can be done when creating AMI's in the AWS console or using the API.
  - Additional volumes can be encrypted.

### Security Groups

  - All Inbound traffic is blocked by default.
  - All Outbound traffic is allowed. 
  - Changed to security Groups take effect **immediately**.
  - You can have any number of EC2 instances within a security group.
  - You can have multiple security groups attached to EC2 instances.
  - Security Groups are **STATEFUL**.
  - If you create an inbound rule allowing traffic in, that traffic is automatically allowed back out again.
  - You cannot block specific IP addresses using Security Groups, instead use Network Access Control Lists.
  - You can specify allow rules, but not deny rules.

### Compare EBS Types

##### 5 Types of EBS Storage

  > gp2, io1, st1, sc1, standard

  - **General Purpose (SSD)** - **gp2** - Balance of price and performance suitable for most workloads.
    > _Volume Size: 1 GiB - 16 TiB, Max IOPS Volume: 16,000_
  - **Provisioned IOPS (SSD)** - **io1** - Highest Performance SSD volume designed for mission-critical applications.
    > _Volume Size: 4 GiB - 16 TiB, Max IOPS Volume: 64,000_
  - **Throughput Optimized HDD** - **st1** - Lost cost HDD volume suitable for Big Data & Data Warehouses
    > _Volume Size: 500 GiB - 16 TiB, Max IOPS Volume: 500_
  - **Cold HDD** - **sc1** - File Servers
    > _Volume Size: 500 GiB - 16 TiB, Max IOPS Volume: 250_
  - **EBS magnetic HDD** - **standard** - Workloads where data is infrequently accessed and not using something like S3 Glacier.
    > _Volume Size: 1 GiB - 1 TiB, Max IOPS Volume: 40-200_
  
### EBS Snapshots

  - Volumes exist on EBS. Think of EBS as a virtual hard disk.
  - **Snapshots exist on S3**. Think of snapshots as a photograph of the disk.
  - Snapshots are point-of-time copies of Volumes.
  - **Snapshots are incremental** -- this means that only the blocks that have changed since your last snapshot are moved to S3.
  - The first snapshot takes some time to create.
  - To create a snapshot for Amazon EBS volumes that serve as root devices, you should stop the instance before taking the snapshot to ensure it is consistent. Though, it can still be taken while the instance is running.
  - You can create AMI's from both Volumes and Snapshots.
  - You can change EBS volume sizes on the fly, including changing the size and storage type.
  - Volumes will **ALWAYS** be in the AZ as the EC2 instance.

### Migrating EBS

  - EC2 AZ change. EC2 volumes can be moved from one AZ to another. To move an EC2 volume, take a snapshot of it, create an AMI from the snapshot, then use the AMI to launch the EC2 instance in a new AZ.
  - EC2 Region change. Take a snapshot of the EC2 volume, create an AMI from the snapshot, copy the AMI from one region to another. Then use the copied AMI to launch the new EC2 instance in the new region.

### EBS vs Instance Store

  - Instance Store Volumes are sometimes called **Ephemeral Storage**.
  - Instance store volumes cannot be stopped. If the underlying host fails, you will lose your data.
  - EBS backed instances can be stopped. You will not lose the data on this instance if it is stopped.
  - You can reboot both, you will not lose your data. 
  - By default, both ROOT volumes will be deleted on termination. However, with EBS columns, you can tell AWS to keep the root device volume.

### CloudWatch

  - CloudWatch is used for monitoring performance.
  - CloudWatch can monitor most of AWS as well as your applications that run on AWS.
  - CloudWatch with EC2 will monitor events every 5 minutes by default.
  - You can have 1 minute intervals by turning on detailed monitoring.
  - You can create CloudWatch alarms which trigger notifications.
  - CloudWatch is all about performance. CloudTrail is all about auditing.
  - Standard Monitoring = 5 Minutes
  - Detailed Monitoring = 1 Minute
  - **What Can I do With CloudWatch?**
    - **Dashboards** - Creates awesome dashboards to see what is happening with your AWS environment.
    - **Alarms** - Allows you to set Alarms that notify you when particular thresholds are hit.
    - **Events** - CloudWatch Events helps you to respond to state changes in your AWS resources.
    - **Logs** - CloudWatch Logs helps you to aggregate, monitor, and store logs.

### The CLI

  - You can interact with AWS from anywhere in the world just by using the command line (CLI)
  - You will need to set up access in **IAM**
  - Commands themselves are not in the exam, but some basic commands will be useful to know for real life.

### Roles 

  - Roles are more secure than storing your access key and secret access key on individual EC2 instances.
  - Roles are easier to manage.
  - Roles can be assigned to an EC2 instance after it is created using both the console & command line.
  - Roles are universal -- you can use them in any region.

### BootStrap Scripts

  - Bootstrap scripts run when an EC2 instance first boots.
  - Can be a powerful way of automating software installs and updates.

### EFS

  - Supports the Network File System version 4 (NFSv4) protocol.
  - You only pay for the storage you use (no pre-provisioning required).
  - Can scale up to the petabytes.
  - Can support thousands of concurrent NFS connections.
  - Data is stored across multiple Availability Zones within a region.
  - Read After Write Consistency.

### EC2 Placement Groups

  - Three Types of Placement Groups
    - **Clustered Placement Group**
      - Low Network Latency / High Network Throughput
    - **Spread Placement Group**
      - Individual Critical EC2 instances
    - **Partitioned**
      - Multiple EC2 instances HDFS, HBase, and Cassandra
  - A clustered placement group can't span multiple Availability Zones.
  - A spread placement and partitioned group can.
  - The name you specify for a placement group must be unique within your AWS account.
  - Only certain types of instances can be launched in a placement group (Compute Optimized, GPU, Memory Optimized, Storage Optimized)
  - AWS recommend homogenous instances within clustered placement groups.
  - You can't merge placement groups.
  - You can't move an existing instance into a placement group. You can create an AMI from your existing instance, and then launch a new instance from the AMI into a placement group.

--- 
### EC2 Quiz:
---

- Can Spread Placement Groups be deployed across multiple Availability Zones?
  - YES.
- When creating a new security group, all inbound traffic is allowed by default.
  - FALSE.
- To help you manage your Amazon EC2 instances, you can assign your own metadata in the form of ________.
  - Tags.
- Which of the following features only relate to Spread Placement Groups?
  - The placement group can only have 7 running instances per Availability Zone.
- In order to enable encryption at rest using EC2 and Elastic Block Store, you must ________.
  - Configure encryption when creating the EBS volume.
- Can I move a reserved instance from one region to another?
  - NO.
- You need to know both the private IP address and public IP address of your EC2 instance. You should ________.
  - Retrieve the instance Metadata from http://169.254.169.254/latest/meta-data/
- Amazon's EBS volumes are ________.
  - Block-based storage.
- If an Amazon EBS volume is an additional partition (not the root volume), can I detach it without stopping the instance?
  - Yes, although it may take some time.
- You can add multiple volumes to an EC2 instance and then create your own RAID 5/RAID 10/RAID 0 configurations using those volumes.
  - TRUE.
- Individual instances are provisioned ________.
  - In Availability Zones.
- Spread Placement Groups can be deployed across multiple Availability Zones
  - TRUE.
- Is it possible to perform actions on an existing Amazon EBS Snapshot?
  - Yes, through the AWS APIs, CLI, and AWS Console.
- The use of a cluster placement group is ideal _______.
  - Your fleet of EC2 instances requires high network throughput and low latency within a single availability zone.
- EBS Snapshots are backed up to S3 in what manner?
  - Incrementally.
- Can I delete a snapshot of an EBS Volume that is used as the root device of a registered AMI?
  - NO.
- Which AWS CLI command should I use to create a snapshot of an EBS volume?
  - aws ec2 create-snapshot
- I can change the permissions to a role, even if that role is already assigned to an existing EC2 instance, and these changes will take effect immediately.
  - TRUE.
- To retrieve instance metadata or user data you will need to use the following IP Address:
  - http://169.254.169.254
- Will an Amazon EBS root volume persist independently from the life of the terminated EC2 instance to which it was previously attached? In other words, if I terminated an EC2 instance, would that EBS root volume persist?
  - Only if I specify (using either the AWS Console or the CLI) that it should do so.
- I can use the AWS Console to add a role to an EC2 instance after that instance has been created and powered-up.
  - TRUE.
- Can you attach an EBS volume to more than one EC2 instance at the same time?
  - NO.

---
### Databases On AWS
---

#### What is a relational database?

  - **Relational Databases** are what most of us are all used to. They have been around since the 70's. Think of a traditional spreadsheet:
    - Database
    - Tables
    - Row
    - Fields (Columns)

#### Relational databases on AWS:

  - SQL Server
  - Oracle
  - MySQL Server
  - PostgreSQL
  - Aurora
  - MariaDB

#### Relational databases services have two key features:

  - **Multi-AZ** - For Disaster Recovery
  - **Read Replicas** - For Performance

#### Non Relational Databases are as follows:

  - Collection
  - Document
  - Key Value Pairs

#### What is Data Warehousing?

  - Used for business intelligence. Tools like Cognos, Jaspersoft, SQL Server Reporting Services, Oracle Hyperion, SAP NetWeaver.
  - Used to pull in very large and complex data sets. Usually used by management to do queries on data (such as current performance vs targets etc.)

#### OLTP vs OLAP

  - **Online Transaction Processing (OLTP)** differs from **OLAP Online Analytics Processing (OLAP)** in terms of the types of queries you will run.

#### What is ElastiCache?

  - **ElastiCache** is a web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud. The service improves the performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying entirely on slower disk-based databases.

  - ElastiCache supports two open-source in-memory caching engines:
    - **Memcached**
    - **Redis**

#### Exam Tips:

  - **Relational Database Services**
    - **SQL**
    - **MySQL**
    - **PostgreSQL**
    - **Oracle**
    - **Aurora**
    - **MariaDB**
  - **DynamoDB (No SQL)**
  - **Red Shift OLAP**
  - **Elasticache**
    - Memcached
    - Redis
  - Elasticache to speed up performance of existing databases (frequent identical queries).
  - **Remember the following points**:
    - RDS runs on virtual machines.
    - You cannot log in to these operating systems however.
    - Patching of the RDS Operating System and DB is Amazon's responsibility
    - RDS is NOT Serverless.
    - Aurora Serverless IS Serverless

---
### RDS Backups, Multi-AZ & Read Replicas
---

#### Back Ups with RDS

  - There are two different types of Backups for RDS:
    - **Automated Backups**
    - **Database Snapshots**
  
#### Automated Backups

  - **Automated Backups** allow yo uto recover your database to any point in time within a "retention period". The retention period can be between one and 35 days.
  - Automated Backups will take a full daily snapshot and will also store transaction logs throughout the day.
  - When you do a recovery, AWS will first choose the most recent daily backup, and then apply transaction logs relevant to that day. This allows you to do a point in time recovery down to a second, within the retention period.
  - **Automated Backups are enabled by default**. The backup data is stored in S3 and you get free storage space equal to the size of your database. So if you have an RDS instance of 10GB, you will get 10GB worth of storage.
  - Backups are taken within a defined window. During the backup window, storage I/O may be suspended while your data is being backed up and you may experience elevated latency.

#### Database Snapshots

  - **DB Snapshots are done manually** (ie they are user initiated). They are stored even after you delete the original RDS instance, unlike automated backups.

### Encryption At Rest 

  - **Encryption at rest** is supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora. 
  - Encryption is done using the AWS Key Management (KMS) service. Once your RDS instance is encrypted, the data stored at rest in the underlying storage is encrypted, as are its automated backups, read replicas, and snapshots.

### What is Multi-AZ?

  - **Multi-AZ** allows you to have an exact copy of your production database in another Availability Zone. AWS handles the replication for you, so when your production database is written to, this write will automatically be synchronized to the stand by database.
  - In the event of planned database maintenance, DB Instance failure, or an Availability Zone failure, Amazon RDS will automatically fail-over to the standby so that database operations can resume quickly without administrative intervention.

##### Multi-AZ is for Disaster Recovery only

  - It is not primarily used for improving performance. For performance improvement, you need Read Replicas.

##### Multi-AZ is available for the following databases

  - SQL Server
  - Oracle
  - MySQL Server
  - PostgreSQL
  - MariaDB

### What Is A Read Replica?

  - **Read Replicas** allow you to have a read-only copy of your production database. This is achieved by using Asynchronous replication from the primary RDS instance to the read replica. You use read replicas primarily for very read-heavy database workloads.

##### Read Replicas are available for the following databases

  - Aurora
  - Oracle
  - MySQL Server
  - PostgreSQL
  - MariaDB

##### Things to know about Read Replicas:
  
  - Used for scaling, not for DR!
  - Must have automatic backups turned on in order to deploy a read replica.
  - You can have up to 5 read replica copies of any database.
  - You can have read replicas of read replicas (but watch out for latency)

#### Exam Tips:

  - **There are two different types of Backups for RDS:**
    - **Automated Backups**
    - **Database Snapshots**
  - **Read Replicas**
    - Can be Multi-AZ.
    - Used to increase performance.
    - Must have backups turned on.
    - Can be in different regions.
    - Can be MySQL, PostgreSQL, MariaDB, Oracle, Aurora.
    - Can be promoted to master, this will break the Read Replica.
  - **Multi-AZ**
    - Used for disaster recovery.
    - You can force a fail-over from one AZ to another by rebooting the Relation database service instance.
  - **Encryption at rest** is supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora. 
  - Encryption is done using the AWS Key Management (KMS) service. Once your RDS instance is encrypted, the data stored at rest in the underlying storage is encrypted, as are its automated backups, read replicas, and snapshots.

---
### DynamoDB
---

  - **Amazon DynamoDB** is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale. It is a fully managed database and supports both document and key-value data models. Its flexible data model and reliable performance make it a great fir for mobile, web, gaming, ad-tech, IoT, and many other applications.

#### The basics of DynamoDB are as follows:

  - Stored on SSD storage
  - Spread across 3 geographically distinct data centres
  - Eventual Consistent Reads (Default)

#### Eventual Consistent Reads

  - Consistency across all copies of data is usually reached within a second. Repeating a read after a short time should return the updated data. (Best Read Performance)

#### Strongly Consistent Reads

  - A **strongly consistent read** returns a result that reflects all writes that received a successful response prior to the read.

#### The basics of DynamoDB are as follows:

  - Stored on SSD storage
  - Spread across 3 geographically distinct data centres
  - Eventual Consistent Reads (Default)
  - Strongly Consistent Reads

---
### Redshift
---

  - **Amazon Redshift** is a fast and powerful, fully managed, petabyte-scale data warehouse service in the cloud. Customers can start small for just .25 cents per hour with no commitments or upfront costs and scale to a petabyte or more for $1,000 per terabyte per year,less than a tenth of most other data warehousing solutions.

  - Data Warehousing databases use different type of architecture both from a database perspective and infrastructure layer.

#### Redshift can be configured as follows:

  - Single Node (160GB)
  - Multi-Node
    - Leader Node
    - Compute Node
  
#### Advanced Compression:

  - Columnar data stores can be compressed much more than row-based data stores because similar data is stored sequentially on disk. Amazon Redshift employs multiple compression techniques and can often achieve significant compression relative to traditional relational data stores. In addition, Amazon Redshift doesn't require indexes or materialized views, and so uses less space than traditional relational database systems. When loading data into an empty table, Amazon Redshift automatically samples your data and selects the most appropriate compression scheme.

#### Massively Parallel Processing (MPP):

  - Amazon Redshift automatically distributes data and query load across all nodes. Amazon Redshift makes it easy to add nodes to your data warehouse and enables you to maintain fast query performance as your data warehouse grows. 

#### Backups

  - Enabled by default with a 1 day retention period.
  - Maximum retention period is 35 days.
  - Redshift always attempts to maintain at least three copies of your data (the original and replica on the compute nodes and a backup in Amazon S3)
  - Redshift can also asynchronously replicate your snapshots to S3 in another region for disaster recovery.

#### Redshift is priced as follows:

  - Compute Node Hours (total number of hours you run across all your compute nodes for the billing period. You are billed for 1 unit per node per hour, so a 3-node data warehouse cluster running persistently for an entire month would incur 2,160 instance hours. You will not be charged for leader node hours; only compute nodes will incur charges.)
  - Backup
  - Data transfer (Only within a VPC)

#### Security Considerations:
  - Encrypted in transit using SSL
  - Encrypted at rest using AES-256 encryption 
  - By default RedShift takes care of key management.
    - Manage your own keys through HSM
    - AWS Key Management Service

## RedShift Availability:

  - Currently only available in 1 AZ
  - Can restore snapshots to new AZs in the event of an outage.

#### Exam Tips:

  - Redshift is used for business intelligence. 
  - Available in only 1 AZ.
  - **Backups**
    - Enabled by default with a 1 day retention period.
    - Maximum retention period is 35 days.
    - Redshift always attempts to maintain at least three copies of your data (the original and replica on the compute nodes and a backup in Amazon S3)
    - Redshift can also asynchronously replicate your snapshots to S3 in another region for disaster recovery.

---
### Aurora
---

  - **Amazon Aurora** is a MySQL-compatible, relational database engine that combines the speed and availability of high-end commercial databases with the simplicity and cost-effectiveness of open source databases.
  - Amazon Aurora provides up to five times better performance than MySQL at a price point one tenth that of a commercial database while delivering similar performance and availability.

#### Things to know about Aurora:

  - Start with 10GB, scales in 10GB increments to 64TB (Storage Autoscaling)
  - Compute resources can scale up to 32vCPUs and 244GB of Memory.
  - 2 copies of your data is contained in each availability zone, with minimum of 3 availability zones. 6 copies of your data.

#### Two Types of Aurora Replicas are available:

  - Aurora Replicas (currently 15)
  - MySQL Read Replicas (currently 5)

#### Backups With Aurora

  - Automated backups are always enabled on Amazon Aurora DB Instances. Backups do not impact database performance.
  - You can also take snapshots with Aurora. This also does not impact on performance.
  - You can share Aurora Snapshots with other AWS accounts.

#### Exam Tips: 

  - 2 copies of your data is contained in each availability zone, with minimum of 3 availability zones. 6 copies of your data.
  - You can share Aurora Snapshots with other AWS accounts.
  - 2 types of replicas available. Aurora Replicas and MySQL replicas. Automated failover is only available with Aurora Replicas.
  - Aurora has automated backups turned on by default. You can also take Snapshots with Aurora. You can share these snapshots with other AWS accounts.

---
### Elasticache
---

  - **Elasticache** is a web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud. The service improves the performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying entirely on slower disk-based databases.

##### ElastiCache supports two open-source in-memory caching engines:

  - **Memcached**
  - **Redis**

#### Exam Tips:

  - Use ElastiCache to increase database and web application performance.

---
### Database Quiz
---

- Which of the following is not a feature of DynamoDB?
  - The ability to store relational-based data.
- What happens to the I/O operations of a single-AZ RDS instance during a database snapshot or backup?
  - I/O may be briefly suspended while the backup process initializes (typically under a few seconds), and you may experience a brief period of elevated latency.
- You can RDP or SSH into an RDS instance to see what is going on with the operating system.
  - FALSE.
- AWS's NoSQL product offering is known as ________.
  - DynamoDB
- Which set of RDS database engines is currently available?
  - Oracle, SQL Server, MySQL, PostgreSQL
- When creating an RDS instance, you can select the Availability Zone into which you deploy it.
  - TRUE.
- RDS Reserved instances are available for multi-AZ deployments.
  - TRUE.
- With new RDS DB instances, automated backups are enabled by default.
  - TRUE.
- In RDS, what is the maximum value I can set for my backup retention period?
  - 35 Days
- If I wanted to run a database on an EC2 instance, which of the following storage options would Amazon recommend?
  - EBS
- How many copies of my data does RDS – Aurora store by default?
  - 6
- MySQL installations default to port number ________.
  - 3306
- If you want your application to check RDS for an error, have it look for an ______ node in the response from the Amazon RDS API.
  - Error
- Which AWS DB platform is most suitable for OLTP?
  - RDS
- Which of the following is most suitable for OLAP?
  - Redshift
- Which AWS service is ideal for Business Intelligence Tools/Data Warehousing?
  - Redshift
- What data transfer charge is incurred when replicating data from your primary RDS instance to your secondary RDS instance?
  - There is no charge associated with this action.
- Under what circumstances would I choose provisioned IOPS over standard storage when creating an RDS instance?
  - If you use online transaction processing in your production environment.
- If you are using Amazon RDS Provisioned IOPS storage with a Microsoft SQL Server database engine, what is the maximum size RDS volume you can have by default?
  - 16TB
- Which of the following AWS services is a non-relational database?
  - DynamoDB
- You are hosting a MySQL database on the root volume of an EC2 instance. The database is using a large number of IOPS, and you need to increase the number of IOPS available to it. What should you do?
  - Add 4 additional EBS SSD volumes and create a RAID 10 using these volumes.
- In RDS, changes to the backup window take effect ________.
  - Immediately
- Amazon's ElastiCache uses which two engines?
  - Redis & Memcached
- When you add a rule to an RDS DB security group, you must specify a port number or protocol.
  - FALSE

