System Design
=============

Resources used:

https://www.youtube.com/watch?v=UzLMhqg3_Wc


## General Notes
- Ask good questions, define the Minimum Viable Product
    - What features to work on
    - How much to scale
- Don't use buzzwords just for the sake of it, if you mention a technology, make sure you know how it works
- Use the "50 thousands foot view" rule. make sure to cover the high level picture that should include all the vital parts of the system, then start diving down into the detail
- Drive discussions, use the 80-20 rule (you should talk 80% of the time)
- Draw systems on a white-board while explaining the technology and the end to end flow out loud

## High level Topics
- Cover what features will be part of the MVP, for example for a messanger app MVP, a feature could be a 1:1 chat option that includes indication whether the recipient received the message 
- APIs - Once you decided on features, you need to think about the different APIs, who will call what and how 
- Availability - need to discuss how much availability is cared about in this case, i.e what happens if a host goes down, and what happens if the DB goes down - things of that nature
- Latency Performance - if it's a background job you don't usually care about that, but if it's a customer facing application, you want the system to be super fast and might consider adding cache and things of that sort
- Scalability - it works for 100 users, but is it gonna scale as we add more users let's say 1000 or even 1000, will the availability and latency remain the same?
- Durability - data can be stored in some store (DB, FS) securely without being lost or compromised 
- Class Diagram - type of questions such as "design an elevator" or "design a parking lot", usually according to OO principles.
- Security & Privacy, could play a central role depending on the use case
- Cost effectiveness - whether the solution is cost effective, is there an alternate solution that will be more effective, as far as cost is concerned

## Dystem Design Concepts 
- Scaling - Vertical (Stronger host(s)) Vs Horizontal (More host(s))
  - Vertical can be more expensive and limited by a single host, but no distributed system problems
  - Horizontal - you can infinitely add more hosts but then you are facing distributed system challenges
  - Usually, horizontal is preferred 
- CAP Theorem - Consistency, Availability, Partition tolerant.
  - Consistency means your read has the most recent write
  - Availability means you will get a response back (most recent or not)
  - Partition tolerance means that the cluster continues to function even if there is a "partition" (communication break) between two nodes (both nodes are up, but can't communicate).
  - Cap theorem means you could only have 2 of the above. so you must go for partition tolerance. the question is whether you choose consistency or availability for the remaining choice.
  - Read more here: https://codahale.com/you-cant-sacrifice-partition-tolerance/
- ACID vs. BASE
  - ACID - Used more in relational databases 
    - Atomic: All operations in a transaction succeed or every operation is rolled back.
    - Consistent: On the completion of a transaction, the database is structurally sound.
    - Isolated: Transactions do not contend with one another. Contentious access to data is moderated by the database so that transactions appear to run sequentially.
    - Durable: The results of applying a transaction are permanent, even in the presence of failures
  - BASE - Used more in no-sql databases
    - Basic Availability: The database appears to work most of the time.
    - Soft-State: Stores don’t have to be write-consistent, nor do different replicas have to be mutually consistent all the time.
    - Eventual consistency: Stores exhibit consistency at some later point (e.g., lazily at read time).
- Data partitioning/sharding - Let's say you have trillion of records to store, it's not possible that 1 trillion records, it's not possible that 1 node will be in charge of all of it... then comes sharding, how do you shard or split this data such that every node is responsible for some of the records.
  - Common approach is consistent hashing
