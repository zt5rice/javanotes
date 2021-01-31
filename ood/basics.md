# Glossary of System design basics

## System Design Basics


## Key Characteristics of Distributed Systems
<details>
<summary>What are Key Characteristics of Distributed Systems?</summary>
    <ul>
       <li> Scalability </li>
       <li> Reliability </li>
       <li> Availability </li>
       <li> Efficiency </li>
       <li> Serviceability or Manageability </li>
    </ul>
</details>

<details>
<summary>What are Horizontal vs. Vertical Scaling? Differences and example? </summary>
    <ul>
       <li> Horizontal - add more servers - Cassandra and MongoDB</li>
       <li> Vertical Scaling - add more resources to the same server - MySQL</li>
    </ul>
</details>

- What is the relationship between reliability and availability?
    - If a system is reliable, it is available. However, if it is available, it is not necessarily reliable.
    

## Load Balancing
- What is load balancing?
    - It helps to spread the traffic across a cluster of servers to improve responsiveness and availability of applications, websites or databases.
    
- Where is the possible location of load balancer?
     - Between the user and the web server
     - Between web servers and an internal platform layer, like application servers or cache servers
     - Between internal platform layer and database.

- What is the benefit of load balancer?
    

## Caching


## Data Partitioning



## Indexes


## Proxies


## Redundancy and Replication


## SQL vs. NoSQL


## CAP Theorem



## Consistent Hashing


## Long-Polling vs WebSockets vs Server-Sent Events

