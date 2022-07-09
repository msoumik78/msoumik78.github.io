---
layout: post
title:  "Best Practices of designing REST API endpoints"
date:   2020-03-05 13:55:23 +0530
categories: MicroServices
---

# How to design the API end points in micro services architecture

In this post, I'm going to list down some of the cardinal rules (or better to say conventions :)) which are universally followed in API design. The benefits of following these very logical conventions are multiple - from ease of maintenance to lack of ambiguity for the consumers of the API.

So let us see what are the most popular conventions :

* **Using Json as the payload format** - both for the request and for the response. However there are use cases for which protobuf as the response produces more compact output. Also there are some high security use cases where encrypted json can be used as the response format.

* **Designing endpoint names with nouns / resources and using the HTTP methods as verbs to indicate what actions the endpoint can expose**
Also normally always using plurals for resource names like customers instead of customer so that user of the API clearly understands that he is dealing with a collection and not individual customer.
    Like     
    /api/v1/customers/5
     - With GET mapping, the same URI can retrieve the customer with 5 as Id
     - With PUT mapping, the same URI can update the customer with 5 as Id
     - With DELETE mapping, the same URI can delete the customer with 5 as Id

      Endpoints should NOT be named as /api/v1/customers/create or /api/v1/customers/delete
			
* **Using query string to filter sort and paginate the data**
 	/api/v1/customers?status=ACTIVE
 
* **Using clear versioning of the apis - so that you do not need to force your end clients to use a specific version like** 

    /api/v1/customers/5
    /api/v2/customers/5
    
*  **Using nesting in API endpoints to show relationships** : Like if there are many groups and each group has a set of customers, you should design like :

	/api/v1/groups/2/customers/5  - With GET mapping, it indicates you retrieve the 5th customer within 2nd group

*  **Returning http status (2XX or 3XX or 4XX or 5xx) code to clearly indicate the type of HTTP response**

    - The client application behaved erroneously (client error - 4xx response code)
    - The API behaved erroneously (server error - 5xx response code)
    - The client and API worked (success - 2xx response code)     
