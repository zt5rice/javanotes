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
    - Users experience faster, uninterrupted service. Users won’t have to wait for a single struggling server to finish its previous tasks. Instead, their requests are immediately passed on to a more readily available resource.
    - Service providers experience less downtime and higher throughput. Even a full server failure won’t affect the end user experience as the load balancer will simply route around it to a healthy server.
    - Load balancing makes it easier for system administrators to handle incoming requests while decreasing wait time for users.
    - Smart load balancers provide benefits like predictive analytics that determine traffic bottlenecks before they happen. As a result, the smart load balancer gives an organization actionable insights. These are key to automation and can help drive business decisions.
    - System administrators experience fewer failed or stressed components. Instead of a single device performing a lot of work, load balancing has several devices perform a little bit of work.

- How does the load balancer choose the backend server?
    - Only choose from health checks.
    - Algorithm:
        - Least Connection Method - when there are a large number of persistent client connections which are unevenly distributed between the servers.
        - Least Response Time Method
        - Least Bandwidth Method
        - Round Robin Method - It is most useful when the servers are of equal specification and there are not many persistent connections.
        - Weighted Round Robin Method -  Servers with higher weights receive new connections before those with less weights and servers with higher weights get more connections than those with less weights.
        - IP Hash 
        
## Caching


## Data Partitioning



## Indexes


## Proxies


## Redundancy and Replication


## SQL vs. NoSQL


## CAP Theorem



## Consistent Hashing


## Long-Polling vs WebSockets vs Server-Sent Events

