# Scalability on web systems
First of all we need to understand what is scalability, and when something is scalable, in this case an entire web system or just a database system.

*Scalability is a way to measure the property of a system to get large changes and/or receive and bear periods of huge demand.*

How our web application responds to a new feature or a growing quantity of users making requests every day will depend of how scalable is. 

---

### There are two types of scalability:
- Vertical:
  - Consists in upgrading your system resources by adding more powerful ones.
- Horizontal:
  - Consists in upgrading your system resources by adding just more resources.
  
To which one should we aim? Generally it is better to aproach a more **horizontal** scalability method rather than a vertical one, because obtaining powerful resources it's always more expensive, and even if it is reliable and secure as an unit, it may lock your system in many ways:

- If it reaches its limit or fails, finding a new addition as good as the current one will be expensive.
- It's more difficult to switch to more modern resources.

The advantages of horizontal scaling are that with more numbers, even if the resources aren't that expensive, and a good communication schema between all the components of the system, you have a more flexible system, that can increase its numbers, upgrade and adapt to some other changes without worrying about the price of the components you have or you need to obtain.

I think a good comparison would be:

`Trying to raid a fortress with 4 giants, relying on their size and strength`.

With: 

`Trying to raid a fortress with a large army and an organized plan`. 

With the giant option, one loss of one giant supposes a bigger loss to the battle, and it's more difficult to find another one to replace it. With the army option, because your "components" are much more numerous and one soldier is not the sole responsible of a big task, its loss is not that shoking to the whole task of raiding a fortress.

---

There are many moments along the processing of a request when an standard web application performance can be lowered, let's see some of them:

- ### Request reception.
- ### Collate query results and return them to the server.
- ### Render the app (HTML).

This three could end in a lowered performance scenario, but generally this can be solved using more than one server, and filtering the incoming requests with a ***load balancer***.

A load balancer is a machine that receives the incoming requests and **has the only function** of; based on a list of available servers and their current workload, distribute those request among those servers.

Some times a bottleneck appears. A bottleneck produces when multiple processes require the same resources to proceed.

To avoid them we should:
- Store in cache data that will rarelly change but will be requested a lot.
- Try to serve limited information to the users while a lower process finishes serving the whole data requested.
- Load balancing software as we saw earlier.

- ### DB querying:
  - Writting data on the database.
  - Reading data form the database.

DB querying it's also a moment when system performance can be lowered and bottlenecks produce.

## Database bottlenecks
 
Databases are usually separated from the server, and because of that there are different methods to avoid them to be problematic:

- ### Database replication:
  
  Database replication consist on having one database as the "*master*" database, and assing to it some other '*slave*' databases.

  This "*master*" database will replicate / copy all its data on the "*slave*" ones.

  The benefit from doing this shines when there are a lot more of **read** request than **write** request on your database.

  Read requests can be distributed among the replicated databases to free the *master* one of that load, where all **read** requests would be done.

  This however has a obvious downside, and another one not that noticeable:

  - This method doesn't increase the *write* speed.
  - There is replication lag.

    Replication lag appears when the data being requested (*read request*) has been wrote on the master database too recently, and the system hasn't replicated it yet to the *slave* database where that data is needed.

---

![SinglePrimaryReplication](https://user-images.githubusercontent.com/71845375/162701962-6fa154be-c984-43e1-9c23-e25feb522ace.png)

---

- ### Database sharding:

  Database sharding consists on working with multiple databases at the same level (not master nor slave) that divide the overall data of the system among themselves.

  This is a good method when rather than having too much requests, the system works with too much data.

  An example would be a system where *objects* are saved, and those are divided among 3 distinct databases:

  - Database 1: objects 1 to 1000.
  - Databse 2: objects from 1001 to 2000.
  - Database 3: objects from 2001 to 3000.

  This approach is very simple, and in fact the database sharding method is generally simple, but it also has downsides that aren't that obvious:

  - Queries become a lot more complex.
  - Relate the data between different databases or *Joins* are nearly imposible to do.
  
---

![1_WOSlzP8PKH8bWQdmI6JnDw](https://user-images.githubusercontent.com/71845375/162702207-e1db60f9-4dd4-4230-871a-8a131167ea82.png)

