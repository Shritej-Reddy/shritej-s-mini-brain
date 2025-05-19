NoSQL, also referred to as “not only SQL” or “non-SQL”, is an approach to database design that enables the storage and querying of data outside the traditional structures found in relational databases.

While NoSQL can still store data found within relational database management systems (RDBMS), it just stores it differently compared to an RDBMS. The decision to use a relational database versus a non-relational database is largely contextual, and it varies depending on the use case.

Instead of the typical tabular structure of a relational database, NoSQL databases, house data within one data structure, such as JSON document. Since this non-relational database design does not require a schema, it offers rapid scalability to manage large and typically unstructured data sets.

NoSQL is also type of distributed database, which means that information is copied and stored on various servers, which can be remote or local. This ensures availability and reliability of data. If some of the data goes offline, the rest of the database can continue to run.  

Today, companies need to manage large data volumes at high speeds with the ability to scale up quickly to run modern web applications in nearly every industry. In this era of growth within cloud, big data, and mobile and web applications, NoSQL databases provide that speed and scalability, making it a popular choice for their performance and ease of use.

### Types of NoSQL databases

NoSQL provides other options for organizing data in many ways. By offering diverse data structures, NoSQL can be applied to data analytics, managing big data, social networks, and mobile app development. 

A NoSQL database manages information using any of these primary data models: 

### Key-value store

This is typically considered the simplest form of NoSQL databases. This schema-less data model is organized into a dictionary of key-value pairs, where each item has a key and a value. The key could be like something similar found in a SQL database, like a shopping cart ID, while the value is an array of data, like each individual item in that user’s shopping cart. It’s commonly used for caching and storing user session information, such as shopping carts. However, it's not ideal when you need to pull multiple records at a time. Redis and Memcached are examples of an open-source key-value databases.

### Document store

As suggested by the name, document databases store data as documents. They can be helpful in managing semi-structured data, and data are typically stored in JSON, XML, or BSON formats. This keeps the data together when it is used in applications, reducing the amount of translation needed to use the data. Developers also gain more flexibility since data schemas do not need to match across documents (e.g. name vs. first_name). However, this can be problematic for complex transactions, leading to data corruption. Popular use cases of document databases include content management systems and user profiles. An example of a document-oriented database is [MongoDB](https://www.ibm.com/products/databases-for-mongodb), the database component of the [MEAN stack](https://www.ibm.com/topics/mean-stack).

Want to know more about MongoBD? Check out the IBM [tutorial](https://cloud.ibm.com/docs/databases-for-mongodb?topic=databases-for-mongodb-getting-started) on getting started with using IBM Cloud Databases for MongoDB. 

### Wide-column store

These databases store information in columns, enabling users to access only the specific columns they need without allocating additional memory on irrelevant data. This database tries to solve for the shortcomings of key-value and document stores, but since it can be a more complex system to manage, it is not recommended for use for newer teams and projects. Apache HBase and Apache Cassandra are examples of open-source, wide-column databases. Apache HBase is built on top of Hadoop Distributed Files System that provides a way of storing sparse data sets, which is commonly used in many big data applications. Apache Cassandra, on the other hand, has been designed to manage large amounts of data across multiple servers and clustering that spans multiple data centers. It’s been used for a variety of use cases, such as social networking websites and real-time data analytics.

### Graph store

This type of database typically houses data from a knowledge graph. Data elements are stored as nodes, edges and properties. Any object, place, or person can be a node. An edge defines the relationship between the nodes. For example, a node could be a client, like IBM, and an agency like, Ogilvy. An edge would be categorize the relationship as a customer relationship between IBM and Ogilvy.

Graph databases are used for storing and managing a network of connections between elements within the graph. [Neo4j](https://neo4j.com/users/ibm/) (link resides outside ibm.com), a graph-based database service based on Java with an open-source community edition where users can purchase licenses for online backup and high availability extensions, or pre-package licensed version with backup and extensions included. 

### In-memory store

With this type of database, like IBM solidDB, data resides in the main memory rather than on disk, making data access faster than with conventional, disk-based databases. 

### Examples of NoSQL databases

Many companies have entered the NoSQL landscape. In addition to those mentioned above, here are some popular NoSQL databases: 

- [Apache CouchDB](https://www.ibm.com/topics/couchdb), an open source, JSON document-based database that uses JavaScript as its query language. 
- [Elasticsearch](https://www.ibm.com/products/databases-for-elasticsearch), a document-based database that includes a full-text search engine. 
- [Couchbase](https://www.ibm.com/blog/getting-started-with-the-couchbase-autonomous-operator-on-ibm-cloud-kubernetes-service/), a key-value and document database that empowers developers to build responsive and flexible applications for cloud, mobile, and edge computing.

NoSQL provides other options for organizing data in many ways. By offering diverse data structures, NoSQL can be applied to data analytics, managing big data, social networks, and mobile app development. 

A NoSQL database manages information using any of these primary data models: 

### Key-value store

This is typically considered the simplest form of NoSQL databases. This schema-less data model is organized into a dictionary of key-value pairs, where each item has a key and a value. The key could be like something similar found in a SQL database, like a shopping cart ID, while the value is an array of data, like each individual item in that user’s shopping cart. It’s commonly used for caching and storing user session information, such as shopping carts. However, it's not ideal when you need to pull multiple records at a time. Redis and Memcached are examples of an open-source key-value databases.

### Document store

As suggested by the name, document databases store data as documents. They can be helpful in managing semi-structured data, and data are typically stored in JSON, XML, or BSON formats. This keeps the data together when it is used in applications, reducing the amount of translation needed to use the data. Developers also gain more flexibility since data schemas do not need to match across documents (e.g. name vs. first_name). However, this can be problematic for complex transactions, leading to data corruption. Popular use cases of document databases include content management systems and user profiles. An example of a document-oriented database is [MongoDB](https://www.ibm.com/products/databases-for-mongodb), the database component of the [MEAN stack](https://www.ibm.com/topics/mean-stack).

Want to know more about MongoBD? Check out the IBM [tutorial](https://cloud.ibm.com/docs/databases-for-mongodb?topic=databases-for-mongodb-getting-started) on getting started with using IBM Cloud Databases for MongoDB. 

### Wide-column store

These databases store information in columns, enabling users to access only the specific columns they need without allocating additional memory on irrelevant data. This database tries to solve for the shortcomings of key-value and document stores, but since it can be a more complex system to manage, it is not recommended for use for newer teams and projects. Apache HBase and Apache Cassandra are examples of open-source, wide-column databases. Apache HBase is built on top of Hadoop Distributed Files System that provides a way of storing sparse data sets, which is commonly used in many big data applications. Apache Cassandra, on the other hand, has been designed to manage large amounts of data across multiple servers and clustering that spans multiple data centers. It’s been used for a variety of use cases, such as social networking websites and real-time data analytics.

### Graph store

This type of database typically houses data from a knowledge graph. Data elements are stored as nodes, edges and properties. Any object, place, or person can be a node. An edge defines the relationship between the nodes. For example, a node could be a client, like IBM, and an agency like, Ogilvy. An edge would be categorize the relationship as a customer relationship between IBM and Ogilvy.

Graph databases are used for storing and managing a network of connections between elements within the graph. [Neo4j](https://neo4j.com/users/ibm/) (link resides outside ibm.com), a graph-based database service based on Java with an open-source community edition where users can purchase licenses for online backup and high availability extensions, or pre-package licensed version with backup and extensions included. 

### In-memory store

With this type of database, like IBM solidDB, data resides in the main memory rather than on disk, making data access faster than with conventional, disk-based databases. 

### Examples of NoSQL databases

Many companies have entered the NoSQL landscape. In addition to those mentioned above, here are some popular NoSQL databases: 

- [Apache CouchDB](https://www.ibm.com/topics/couchdb), an open source, JSON document-based database that uses JavaScript as its query language. 
- [Elasticsearch](https://www.ibm.com/products/databases-for-elasticsearch), a document-based database that includes a full-text search engine. 
- [Couchbase](https://www.ibm.com/blog/getting-started-with-the-couchbase-autonomous-operator-on-ibm-cloud-kubernetes-service/), a key-value and document database that empowers developers to build responsive and flexible applications for cloud, mobile, and edge computing

### Advantages of NoSQL 

Each type of NoSQL database has strengths that make it better for specific use cases. However, they all share the following advantages for developers and create the framework to provide better service customers, including: 

- **Cost-effectiveness:** It is expensive to maintain high-end, commercial RDBMS. They require the purchase of licenses, trained database managers, and powerful hardware to scale vertically.  NoSQL databases allow you to quickly scale horizontally, better allocating resources to minimize costs. 

- **Flexibility:** Horizontal scaling and a flexible data model also mean NoSQL databases can address large volumes of rapidly changing data, making them great for agile development, quick iterations, and frequent code pushes. 

- **Replication:** NoSQL replication functionality copies and stores data across multiple servers. This replication provides data reliability, ensuring access during down time and protecting against data loss if servers go offline. 

- **Speed:** NoSQL enables faster, more agile storage and processing for all users, from developers to sales teams to customers. Speed also makes NoSQL databases generally a better fit for modern, complex web applications, e-commerce sites, or mobile applications.

### NoSQL use cases 

The structure and type of NoSQL database you choose will depend on how your organization plans to use it. Here are some specific uses for various types of NoSQL databases. 

- **Managing data relationships:** Managing the complex aggregation of data and the relationships between these points is typically handled with a graph-based NoSQL database. This includes recommendation engines, knowledge graphs, fraud detection applications, and social networks, where connections are made between people using various data types. 

- **Low-latency performance:** Gaming, home fitness applications, and ad technology all require high throughput for real-time data management. This infrastructure provides the greatest value to the consumer, whether that’s market bidding updates or returning the most relevant ads. Web applications require in-memory NoSQL databases to provide rapid response time and manage spikes in usage without the lag that can comes with disk storage. 

- **Scaling and large data volumes:** E-commerce requires the ability to manage huge spikes in usage, whether it’s for a one-day sale or the holiday shopping season. Key-value databases are frequently used in e-commerce applications because its simple structure is easily scaled up during times of heavy traffic. This agility is valuable to gaming, adtech, and Internet of Things (IoT) applications.

### Microservices and NoSQL databases 

The need for large companies to provide services without latency and to scale more quickly has spurred growth for microservices, which has led companies to examine [what type of database to use](https://www.ibm.com/blog/choosing-the-right-databases-for-microservices/) for different applications. 

Companies have found that using a single, relational database for every component of an application has its limitations, especially when better alternatives exist for specific components. [Microservices](https://www.ibm.com/topics/microservices) are an attractive option, in part, because they eliminate the need for a single, shared data store for an entire application. Instead, the application has many, loosely coupled and independently deployable services, each with their own data model and database, and integrated via API gateways or an [iPaaS](https://www.ibm.com/topics/ipaas). 

The pattern of using multiple databases within a single application, also known as polyglot persistence, has helped to create space in the market for NoSQL databases to thrive. Today, developers can leverage the right database for the right microservice without trying to make everything work in the context of a single, relational database.