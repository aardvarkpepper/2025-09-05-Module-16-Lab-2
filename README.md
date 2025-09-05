## Reflection

1.  The Over-fetching Problem: In your own words, explain the concepts of “over-fetching” and “under-fetching” in the context of a REST API. How does GraphQL’s query language inherently solve this problem?

REpresentational State Transfer (REST) returns fixed data sets typically based on pre-programmed parameters.  GraphQL returns only specifically what a user requests.

Mongoose can use projections to address this in part, receiving only a subset of data stored in a document.  https://mongoosejs.com/docs/api/model.html#Model.find().

But where GraphQL can send a single query for a user and their posts, REST would typically send one query for a user and another query for their posts.

2.  Endpoint and Schema Philosophy: Compare the endpoint structure of a typical REST API with that of a GraphQL API. How does GraphQL’s strongly-typed schema benefit frontend developers?

REST endpoint: HTTP method, Header, Body.

GraphQL endpoint:  specific requested fields.

With GraphQL, frontend developers get only requested data, so don't have to deal with potential issues (bugs) from unrequested data, multiple queries, how to pass multiple queries, changes in program or data strucure requiring updates.  With GraphQL, developers request specific data and get specific data.

3.  Caching and Complexity: Caching is often cited as a major advantage of REST. Explain why caching is simpler in REST compared to GraphQL. What is a use case where the flexibility of GraphQL might outweigh its caching complexity?

REST responses can use HTTP caching mechanisms for caching requests (ETags, cache-control headers).  GraphQL doesn't leverage HTTP caching mechanisms, Each GraphQL query can be unique, so field-level caching or custom cache management solutions are typical.

Suppose an app is designed for business owners with highly individual needs.  One business owner might want to generate a report with overall sales of a product, sales in genres broken further down by category, regional economic indicators, sales predictions in an area, economic forecasts, and so on.  Though the business owner only wants to generate a single report to read, a RESTful API would need to make dozens of requests to compile then handle all the different information, each request carrying a transaction cost.  A GraphQL query, though, could get all that information in a single request (or at the least, reduced requests).