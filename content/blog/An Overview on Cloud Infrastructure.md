---
title: "An Overview on Cloud Infrastructure"
date: 2024-05-23
lastmod: 2024-08-12
tags: ["Computer Science"]
author: ["Ali Hindy"]
description: "A brief overview of the cloud infrastructure ecosystem."
summary: "A brief overview of the cloud infrastructure ecosystem."
showToc: false
disableAnchoredHeadings: false
---

- One of the biggest shifts in the early 2000s that ended up significantly advancing technological development was the transition from on-premises computing to cloud computing. This transition meant that instead of hosting and maintaining physical servers, you could pay someone else to do it, which came with three big advantages: cost-efficiency, scalability, and accessibility.
    - Cloud computing eliminated the need for upfront costs related to hardware and constant maintenance of your hardware, as well as allowing organizations and individuals to scale their applications easily (just by adding more compute). Additionally, this network of global data centers allowed for more accessibility, as anyone could remotely access resources given the proper credentials and an internet connection.
- Companies like Box and Dropbox (Box on the enterprise side, Dropbox on the consumer side) took many companies from on-premises computing to the cloud, with an emphasis on file storage and access. As cloud computing grew in popularity, there became an increased demand for many different functionalities, from different types of databases to different types of networks.
- The current cloud computing ecosystem consists of three main competitors, who all offer similar (if not the exact same) products: Google Cloud, Microsoft Azure, and Amazon Web Services (AWS).
    - Each of these providers give users a vast range of cloud functionality, but they can all be divided into two different business models: Serverless and Containers
    - In a **serverless** model, the cloud provider manages your infrastructure and automatically manages the relevant resources that you need. Examples include AWS Lambda and Google Cloud Functions.
    - In a **containerized** model, the cloud provider gives you just a server or multiple servers where you can write and deploy your code.
        - For example, imagine you are building an app that allows users to upload an image. In a serverless model, all you have to do is write the code that allows a user to upload an image, and create an event trigger like an HTTP request. Then, if you deploy the function to a serverless platform like AWS, the function executes whenever there is an event trigger and AWS handles any resizing or database manipulation that needs to occur.
            - AWS makes money here by charging you for the time when the code is running and the amount of resources (servers) you use.
        - In a containerized model, you have to build all of this infrastructure yourself, essentially handling all of the resource scaling and event triggers yourself.
            - AWS makes money here by charging you for the server to run your code and all of the resources you use. Either way, AWS is making money off of you!
- In both of these models, you rely on the cloud provider heavily for all of your compute operations. If AWS goes down, so will your website. However, these centralized cloud providers have poured a ton of energy and resources into making their systems fault tolerant and reliable.
- This is in part due to the fact that their technology stack is actually quite simple. They build on top of Open Source platforms like Xen and Linux-based operating systems and package them in such a way that is reliable and accessible for users.
- As the “big three” grew, the amount of complexity with these cloud functions and all of the availability grew exponentially. Many companies spawned in order to make cloud computing simpler and more cost-effective for enterprises, like Databricks (which originally started as a platform for distributed cloud computing), Snowflake (a cloud-native data warehouse solution for managing large amounts of data), and Datadog (a data analytics platform for the cloud)
- In the age of AI, cloud computing has become increasingly more important in order to facilitate large scale training of massive models like GPT-4, LLama-2, and more. More startups have emerged to address the problem of training models in the cloud, like Modal.com, a serverless platform for data-intensive applications.



Technical Overview:

- At the core of cloud computing lies two main components: databases and compute. At the time of writing, there are hundreds of different database and compute solutions, each with their strengths and weaknesses, and I will cover the most popular ones.
- Databases:
    - As the name suggests, a database is a collection of data stored on a server, typically managed by something called a Database Management System (DBMS). The DBMS allows us to interact with our data, inducing read/write operations on our data.
    - Key-Value Database:
        - Examples: Redis
        - Use Cases: Cache layer (quick storage for fast reads)
        - Description: A key-value database follows the format that the name suggests, where you have some key, say a “user_id” and a value, such as “info.” The key-value functions exactly like a dictionary in Python or a JSON object, and allows for fast data lookup.
    - Wide Column Database:
        - Examples: Cassandra, Apache HBBase
        - Use Cases: More complex caching
        - Description: A wide-column database follows the same format of the wide-column database, except that instead of the key linking to one value, the key links to a vector of values.
    - Document Oriented Database:
        - Examples: MongoDB, Firestore, CouchDB
        - Use Cases: Unstructured data
        - Description: Document oriented databases allow significant flexibility with data where the structure evolves or you are unsure of the structure, and allows you to link collections of documents (usually JSON objects, but can be anything) to other collections of documents.
    - Relational Database:
        - Examples: MySQL, Postgres SQL, SQL Server, Cockroach DB
        - Use Cases: Structured data
        - Description: Think of an Excel sheet. This is the standard format for a relational database, where you have, in the simplest case, a table with columns corresponding to values. You can also add multiple tables and join them with a common column.
    - Graph Database:
        - Examples: Neo4j, DGraph
        - Use Cases: Dynamic data, i.e. social networks
        - Description: When you want to model data using a graph, it is likely best to use a graph database, where you can model each data point with a node and edges connecting each node.
    - Multi-Model Databases:
        - Examples: FaunaDB, Couch, CosmosDB
        - Use Cases: Database optimization, looking to minimize cost and optimize storage
        - Description: A hybrid of all of the previously mentioned models, allowing for customization and storage/space/lookup optimization