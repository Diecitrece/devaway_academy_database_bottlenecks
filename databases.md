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

- Request reception.
- Collate query results and return them to the server.
- Render the app (HTML).

This three could end in a lowered performance scenario, but generally this can be solved using more than one server, and filtering the incoming requests with a ***load balancer***.

A load balancer is a machine that receives the incoming requests and **has the only function** of; based on a list of available servers and their current workload, distribute those request among those servers.

- DB querying
  - Writting data on the database.
  - Reading data form the database.

## Database bottlenecks
 
# THIS IS WORK IN PROGRESS, I WILL FINISH IT MONDAY'S MORNING
