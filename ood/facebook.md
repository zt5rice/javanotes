# Facebook Newsfeed

1. What is Facebook’s newsfeed?
Function: constantly updating list of stories in the middle of Facebook’s homepage.
Components: status updates, photos, videos, links, app activity, and ‘likes’ from people, pages, and groups that a user follows on Facebook. 
Application: newsfeed system in social media site you design - Twitter, Instagram, or Facebook

2. Requirements and Goals of the System
Functional requirements: 
Newsfeed will be generated based on the posts from the people, pages, and groups that a user follows. 
Users have many friends AND pages/groups.
Feeds may contain images, videos, or just text. 
support appending new posts as they arrive to the newsfeed for all active users. 
Non-functional requirements: 
real-time newsfeed - latency < 2s. 
A post < 5s, assuming a new newsfeed request comes in.

3.Capacity Estimation and Constraints
Assume on average a user  - 300 friends and follows 200 pages. 
Traffic estimates: 
300M daily active users * 5 fetch/day = 1.5B newsfeed/day = 17.5 k/sec. 
Storage estimates: 
In memory: around 500 posts/user * 1KB/post = 500KB/user* 300M users = 150TB of memory. 
Machine #: 150TB of memory / 100GB/server = 1500 machines

4. System APIs
SOAP or REST APIs to expose the functionality of our service. 
      getUserFeed(api_dev_key, user_id, since_id, count, max_id, exclude_replies)

Parameters: 
api_dev_key (string): The API developer key of a registered can be used to, among other things, throttle users based on their allocated quota. 
user_id (number): The ID of the user for whom the system will generate the newsfeed.
since_id (number): Optional; returns results with an ID higher than (that is, more recent than) the specified ID. 
count (number): Optional; specifies the number of feed items to try and retrieve up to a maximum of 200 per distinct request. 
max_id (number): Optional; returns results with an ID less than (that is, older than) or equal to the specified ID. 
exclude_replies(boolean): Optional; this parameter will prevent replies from appearing in the returned timeline. 
Returns: (JSON) Returns a JSON object containing a list of feed items.


5. Database Design
There are three primary objects: User, Entity (e.g. page, group, etc.), and FeedItem (or Post). entities relationships between these : 
A User can follow other entities and can become friends with other users. 
Both users and entities can post FeedItems which can contain text, images, or videos. 
Each FeedItem will have a UserID which will point to the User who created it. 
Each FeedItem can optionally have an EntityID pointing to the page or the group where that post was created. 
Relational database-> User-Entity relation and FeedItem-Media relation?
Separate table:  friend-friend/entities relationship /FeedMedia relation.




6. High Level System Design: 

- Feed generation: 
    - Retrieve IDs of all users and entities that xxx follows. 
    Retrieve latest, most popular and relevant posts for those IDs. 
    Rank these posts based on the relevance to xxx. This represents Jane’s current feed. 
    Store this feed in the cache and return top posts (say 20) to be rendered on Jane’s feed. 
    On the front-end, when Jane reaches the end of her current feed, she can fetch the next 20 posts from the server and so on. One thing to notice here is that we generated the feed once and stored it in the cache. 
    new incoming posts from people that XXX follows? 
    online - mechanism to rank and add to feed. We can periodically - notified newer items

- Feed publishing: 
    Web servers - maintain a connection with the user.
    Application server -  storing new posts in the database servers
    Metadata database and cache: To store the metadata about Users, Pages, and Groups. 
    Posts database and cache: To store metadata about posts and their contents. 
    Video and photo storage, and cache: Blob storage, to store all the media included in the posts.
    Newsfeed generation service: To gather and rank all the relevant posts for a user to generate newsfeed and store in the cache. This service will also receive live updates and will add these newer feed items to any user’s timeline. 
    Feed notification service: To notify the user that there are newer items available.




7. Detailed Component Design

    a. Feed generation
        To improve the efficiency, we can pre-generate the timeline and store it in a memory.
        Crazy slow for users with a lot of friends/follows - sorting/merging/ranking of a huge number of posts. 
        generate the timeline when loading their page. - quite slow and have a high latency. 
        For live updates,status update ->all followers feed updates ->high backlogs in our Newsfeed Generation Service. 
        For live updates, the server pushing (or notifying about) newer posts to users could lead to very heavy loads.
        Offline generation for news feed:
        servers need to generate the feed for a user -> store FeedItemIDs in a data structure similar to Linked HashMap or TreeMap;

    b. Feed publishing
        "Pull" model or Fan-out-on-load
        "Push" model or Fan-out-on-write
        Hybrid
        we can stop pushing posts from users with a high number of followers (a celebrity user)
        For celebrity users, we can let the followers pull the updates.

    How many feed items can we return to the client in each request? 
    Should we always notify users if there are new posts available for their newsfeed?

8. Feed Ranking 
    - rank by the creation time of the posts. 
    - The high-level idea calculates a final ranking score.
    - Relevant to the importance of any feed item. 
    - Advanced system by constantly evaluating if we are making progress in user stickiness, retention, ads revenue, etc.

9. Data Partitioning
    - Sharding posts and metadata
    distribute our data onto multiple machines such that we can read/write it efficiently
Sharding feed data
we can partition it based on UserID. We can try storing all the data of a user on one server.

Appendix: 
