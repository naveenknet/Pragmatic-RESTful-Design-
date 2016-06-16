Problem Statement : How to solve a problem when the same URI Resource is been consumed by different clients who would want custom RESTful Response

For quite some time we have been hearing lot of  Partial Response and Partial Request for Resources, Lets try to understand the subtle notions.

Partial Response is another way improve the performance of your API calls is by sending and receiving only the portion of the data that you're interested in. This lets your application avoid transferring, parsing, and storing unneeded fields, so it can use resources including network, CPU, and memory more efficiently.

There are two types of partial requests:

a. Partial response: A request where you specify which fields to include in the response (use the fields request parameter).
b. Patch: An update request where you send only the fields you want to change (use the PATCH HTTP verb).


Partial response

By default, the server sends back the full representation of a resource after processing requests. For better performance, you can ask the server to send only the fields you really need and get a partial response instead.
To request a partial response, we can use custom request parameter to specify the fields you want . You can use this parameter with any request that returns response data. 

Few of the leading organizations have pioneered different ways including Google who pioneered the idea of partial response.

LinkedIn

/people:(id,first-name,last-name,industry)

This request on a person returns ID, first name, last name, and industry.

LinkedIn uses this terse :(...) syntax which isn't self-evident. Plus it's difficult for a developer to reverse engineer the meaning using a search engine. But this is the way that LinkedIn does partial selection.

Facebook

/tom/friends?fields=id,name,picture

Google

?fields=title,media:group(media:thumbnail)

With such various recipies it is upto the developer to understand what best can be given to the client which could be more self evident. Implementing the Partial response could be one important task and should be de-coupled from the REST framework being used , else which involves lot of boiler plate code for given Resource and URI. Typically with Cloud providers such as Google App Engine, they provide out of the box Scripts for field parsers which could be customly implemented.

--------------------------------------------------------------------------

Patch (partial update) [new Verb in HTTP Spec ]

You can also avoid sending unnecessary data when modifying resources. To send updated data only for the specific fields that you’re changing, use the HTTP PATCH verb. 

The body of the patch request includes only the resource fields you want to modify,It can be a useful practice to start by retrieving a partial response with the data you want to modify.

Courtesy/References : 
1. https://developers.google.com/
2. API Gateway : Apigee Documentation

