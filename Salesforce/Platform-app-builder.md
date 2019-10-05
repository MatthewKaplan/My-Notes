## Salesforce Platform App Builder Certification

**About the Exam**

  - 60 multiple-choice questions 
  - 90 minutes allotted to complete the exam
  - 63% is the passing score
  - $200 fee
  - $100 retake

---
### Salesforce Fundamentals
---

#### Multi-tenant Architecture Overview

  - Salesforce is a multi-tenant architecture and environment you share resources with other salesforce customers.

#### MVC Design Pattern

  - **Model View Controller**

##### MODEL

  - The **model is your database objects in Salesforce**. The include the standard Salesforce objects like Leads, Contacts, Accounts, Opportunities etc but it also includes any custom objects you've created. Think of it like this - **the "model" represents your data model in terms of MVC**.

##### VIEW

  - **Pages** - While often just called "pages", what we are talking about is **Visualforce pages**. They are the building blocks of the user interface. Visualforce uses HTML to lay out the appearance of the application interface. Each page is referenced by a unique URL just like a regular webpage. The pages themselves also contain Visualforce Components which can be invoked by simple tags inside the page. 
  - **Components** - these are both standard and custom Visualforce Components. Think of them like widgets that you can add to your pages. Once you write the code once, you can reuse it on multiple pages. Components are important because they allow for this reuse. Components can be styled with CSS.

##### CONTROLLER

  - **Controllers** are the building blocks of the actual application logic. The controllers are written in Apex code and they end up controlling and enforcing all the business logic. Remember that one of the key design elements of MVC is to separate the logic from the UI. The presentation layer (the view) shouldn't be mixed with a bunch of business logic. Pages interact with the controller through components which shuttle the data and specifies what happens when the user actually interacts with the UI. Salesforce has pre-built controllers for many of the standard actions like View, Edit, Save.

### The Salesforce Schema 

  - The various objects and their relationships of a Salesforce application can be easily viewed using the Schema builder. And just not viewing, but we can also design, modify and implement new data models using schema builder.

  - Schema builder has a drag and drop interface which is used to perform all the activities. It shows all the relevant details like - field values, data types, relationship with directions etc.

#### App Exchange Sample Exam Question:

  - **Universal Containers has limited in-house development resources, but would like to support online payment processing for its products. What is the recommended solution to meet this requirement?**
    - Install an AppExchange product to provide Payment Gateway processing.

---
### Data Modeling and Management
---

### Let's Talk About Objects

  - The beauty of salesforce is that it is an **object oriented system** that doesn't require a lot of coding in order to get things accomplished on the platform.

  - **Standard Objects** - Accounts, contacts, opportunities, cases, leads, campaigns, activities, products, price books, orders, etc.

  - **Custom Objects** - Any object that you create on the platform and an object can be literally anything. (Survey object)
