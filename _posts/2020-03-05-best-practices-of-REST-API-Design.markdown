---
layout: post
title:  "Best Practices of REST API Design"
date:   2020-03-05 13:55:23 +0530
categories: MicroServices
---


* Use Json as the payload format - specifically from server side indicate that the content type is application/json
* Design endpoint names with nouns / resources and use the HTTP methods as verbs to indicate what actions the endpoint can have
	Also normally use plurals for resource names like customers instead of customer below so that user of the api understands that he is dealing with a collection and not individual customer.
    Like     
    /api/v1/customers/5
     - With GET mapping, you can retrieve the customer with 5 as Id
     - With PUT mapping, you can update the customer with 5 as Id
     - With DELETE mapping, you can delete the customer with 5 as Id


   Now for the same endpoint
	/api/v1/customers/ - With POST mapping, you can create customer by passing the customer as json in request body

 You should not name endpoint as /api/v1/customers/create
			

* Use query string to filter , and sort and paginate the data
 	/api/v1/customers?status=ACTIVE
 
* version the apis clearly - so that you do not need to force your end clients to use a specific version like 

    /api/v1/customers/5
    /api/v2/customers/5
    
*  Use nesting in API endpoints to show relationships : Like if there are many groups and each group has a set of customers, you should design like :

	/api/v1/groups/2/customers/5  - With GET mapping, it indicates you retrieve the 5th customer within 3nd group


*  Return http status code to clearly indicate the http response like use X in Spring boot

    - The client application behaved erroneously (client error - 4xx response code)
    - The API behaved erroneously (server error - 5xx response code)
    - The client and API worked (success - 2xx response code)     


