## AWS Solutions Architect Associate

##### Exam Blueprint

- 130 minutes in length
- 60~ questions 
- Multiple Choice
- Results are between 100-1000 with a passing score of 720
- Qualification is valid for 2 years
- Scenario based questions

### Overview of AWS

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

#### Identity Access Management (IAM) 101

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