# presentation MongoDB

MongoDB is a cross-platform document-oriented database program. 
Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemata.
The main purpose of MongoDB is that it should be productive and scalable.

##(Slide)

The first thing I would like to highlight is a flexible scheme.
Any JSON can be put into the database. 

##(Slide)

MongoDB has no joins. because they harm scalability.
Instead, MongoDB offers data denormalization.

##(Slide)

MongoDB has no transactions
Because it also interferes with scalability, instead there are atomic updates at the document level
This means that the document cannot be partially saved.Either all or nothing.Instead of saving the entire document, you can perform atomic operations. In this case, we update only one field Users

##(Slide)

MongoDB has indexes.
There are as usual, and increasing, decreasing, composite, unique

##(Slide)

Map-reduce is a data processing paradigm for condensing large volumes of data into useful aggregated results. 

We have some raw data.

We want to count how many comments each user posted and the total number of likes he received.

For this we need a function mapper

For this we need a function. The mapper() function receives the document and makes from it a certain projection. In this case, we are projecting likes from the user object. The emit() function takes two parameters (key, value) and groups the values by key.

After the function has passed through the entire document, the values are transferred to reducer ()

The reducer() function receives two parameters key and an array of values grouped by key.
Then a very simple calculation and return the result.
Now we have a function and the function we call execute, indicating the source collection, the collection where to send the result.

So we get the following result

##(Slide)

MongoDB GridFS - rules for storing large files in the MongoDB database. GridFS allows you to store files larger than 16Mb (the maximum document size in MongoDB) through the use of collections. GridFS splits large files into small pieces. These parts are stored in one collection (fs.chunks), and the metadata about a file in another collection (fs.files). When a file request is made, GridFS makes a request to the collection with parts of the file and then returns the entire file.

##(Slide)

Sharding is a method for distributing data across multiple machines. MongoDB uses sharding to support deployments with very large data sets and high throughput operations.

 A MongoDB sharded cluster consists of the following components:
	*	shard: Each shard contains a subset of the sharded data. Each shard can be deployed as a replica set.
	*	mongos: The mongos acts as a query router, providing an interface between client applications and the sharded cluster.
	*	config servers: Config servers store metadata and configuration settings for the cluster. As of MongoDB 3.4, config servers must be deployed as a replica set (CSRS).