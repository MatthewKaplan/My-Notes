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