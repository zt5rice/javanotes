# Web Crawler
1. What is a web crawler? (网络蜘蛛/爬虫)
program browses the World Wide Web in a methodical and automated manner
Examples and Applications: 
News digest;
Search engines application to update data
Create index for some purpose: search engine - faster searches by downloading all pages
Mirror websites / Monitor website changes  
		
2. Requirement for design - scalability and extensibility
scalability - for larger demands up to 10 billion pages
					100k 
extensibility - possible for adding new functions

3. Design consideration:
only HTML pages, not audio/video or other media
only HTTP protocol, FTP not accepted;
expected number of pages ? 1 billion! 10,000
Will deal with Robot exclusion - download authority txt file from target website

4. Capacity estimation and constraints
Processing speed: 15 B / 4 weeks = 6.2 kpages/s
100k / 60.0s = 1.6 kpages/s
Storage: 
assume 100 kB/page + 500 byte meta data = (100k + 500)*15 b = 1.5PB
(100k + 500)*100 k  = 10GB
70% storage capacity model: 1.5 / 0.7 = 2.14 PB
10GB / 0.7 = 14.3 GB

5. High level design

    - URL frontier - list of url (to download), determine future crawling sequence
    - HTML fetcher - retrieve webpage from server
    - Extractor - extract link from HTML
    - Duplicate eliminator - remove unintentionally duplicated web extraction
    - Data store - store retrieved pages, URL and metadata;

    a. How to crawl?
       
       - DFS v.s. BFS: BFS usually used, except some special cases;

    b. Why BFS/DFS?
    
        - Path-ascending crawling? e.g. http://a.com/b/c.html, search http://a.com/b, http://a.com/ 

    c. Difficulty/Challenges in implementing a web crawler?
    
        - large volume of web pages - need intelligent to prioritize download;
        - Rate of change on web pages


6. Detailed component design

    - Module definition:
        - URL frontier - list of url (to download), determine future crawling sequence
        - The fetcher module -  to download the document corresponding to a given URL using the appropriate network protocol like HTTP. (robot’s exclusion rule here)
        - DIS (Document input stream) - cache the ENTIRE small document (<64 kB) locally using an abstraction; 				reread doc is possible.If larger, temporally writes to a backing file; a thread <->DIS; Hence reuses many times. Thread passes DIS to all relevant processing modules;
        - Document dedupe test -> same doc but on different server - use checksum (MD5/SHA) of processed doc stored in database; 	How big is the checksum store? 15billion*8bytes = 120GB; 	Why checksum stores in database? 120GB too large!!! check existence in memory.
        - URL filters: provides a customizable way to control the set of URLs that are downloaded.
        - DNS  - Before connecting, a Web crawler must use the Domain Name Service (DNS) to map the Web server’s hostname into an IP address.
        - URL dedupe test: While extracting links, any Web crawler will encounter multiple links to the same document. 			To reduce the number of operations on DB,  keep an in-memory cache of popular URLs on each host shared by all threads;		Space for URL store: 4 bit checksum -> 15 billion * 4 bytes = 60 GB;									Bloom filter for deduping? Hashing yields false positive -> missing URL to frontier.
        - Checkpointing: avoid failure in weeks’ completing time. 		Action - write regular snapshots of state to disk -> restore easily from last checkpoint.

    - Fault tolerance
        Tool:  consistent hashing for distribution among crawling servers
        Application: 
        replacing a dead host 
        distributing load among crawling servers.
        Data partitioning

     - three kinds of data: 
        1) URLs to visit 
        2) URL checksums for dedupe 
        3) Document checksums for dedupe.

    - Distributing URLs based on hostname -> In each host, stores URL to visit, above three data;

    - To increase availability ->Check host periodically, dump  snapshots of all data to remove servers.

    - Crawler traps
        a URL or set of URLs that cause a crawler to crawl indefinitely.
    - Application:
        - Anti-spam trap for privacy protection;
        - Boost search rating by catching search engine crawler;

    - Appendix:
        How to implement multiple thread web crawlers? Why?



- Additional information:
	Some algorithm questions for practice:
https://leetcode.com/problems/web-crawler/
	https://leetcode.com/problems/web-crawler-multithreaded/
	


