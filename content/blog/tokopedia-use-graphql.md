---
title: "How Tokopedia-Lite use GraphQL"
date: 2019-06-08T06:16:38+07:00
draft: false
---

![](https://cdn-images-1.medium.com/max/1600/1*RXwEHBw0ho2QdvJDPXYfrQ.png)
<span class="figcaption_hack">[https://www.bram.us/2017/06/27/full-stack-react-graphql-tutorial/](https://www.bram.us/2017/06/27/full-stack-react-graphql-tutorial/)</span>

At Tokopedia, we implement a lot of smart technology to achieve customer
satisfaction. GraphQL is one of the technologies we implemented to that end.

### **GraphQL**

Before we explain about how we implemented it in Tokopedia, we’ll explain what
GraphQL is. We have the following summary from GraphQL official website.

![](https://cdn-images-1.medium.com/max/2400/1*LLRdzY68HCRen0CcXEUAAQ.png)
<span class="figcaption_hack">[https://graphql.org/](https://graphql.org/)</span>

> GraphQL is a query language for APIs and a runtime for fulfilling those queries
> with your existing data. GraphQL provides a complete and understandable
description of the data in your API, gives clients the power to ask for exactly
what they need and nothing more, makes it easier to evolve APIs over time, and
enables powerful developer tools.

Basically, GraphQL is a new paradigm provided by Facebook for fetching data from
server to client. GraphQL can combine with existing REST API. GraphQL exists not
to replace REST, but to solve problems that can’t be solved by REST.

![](https://cdn-images-1.medium.com/max/1600/1*EvOapsUz4cmXMIWgTHsTyQ.png)
<span class="figcaption_hack">GraphQL combined with Existing API</span>

*****

### **Tokopedia-Lite**

Tokopedia-Lite is light version from tokopedia mobile site. In the beginning,
tokopedia mobile site was built with Perl. To achieve customer satisfaction, we
decided to revamp our mobile site, and rebuild it with ReactJS. Following is the
Technology stack used by Tokopedia-Lite:

1.  ReactJS
1.  Webpack
1.  GraphQL (We use [Apollo](https://www.apollographql.com/) for client and server)
1.  EmotionJS
1.  Babel
1.  etc

***NB**: Another article will explain more deep about Tokopedia-Lite

![](https://cdn-images-1.medium.com/max/1600/1*yvxAy82JOYbyNGefj1v01Q.png)
<span class="figcaption_hack">Tokopedia-Lite Journey</span>

*****

### **GraphQL — Tokopedia-Lite**

At Tokopedia, we have multiple Tribes each having their own focus area. For
example, Tribe Discovery focuses on helping the user easily find products in
marketplace. Tribe Digital focuses on selling digital products like recharge
(pulsa), train ticket, event ticket, etc. Therefore, in one page, we may need to
call multiple different APIs from different teams.

![](https://cdn-images-1.medium.com/max/1600/0*p9hMktoHzz5FGbwp.)
<span class="figcaption_hack">Tokopedia-Lite & GraphQL Architecture</span>

*****

### **Home Case**

![](https://cdn-images-1.medium.com/max/1600/1*xqULPbGkGEALfrkhJc5Mpg.png)
<span class="figcaption_hack">Home Tokopedia-Lite</span>

If we look the image, at Home page Tokopedia-Lite, we need to make calls to 5
different API at the very least. If Tokopedia-Lite hadn’t used GraphQL, then
there would be 5 round trip network between client and server and that would
make our home page slow, and make the user wait too long to get our home page
rendered completely. However, because we use GraphQL in Tokopedia-Lite, our
client only needs one API call to server and the GraphQL server does the rest
(do 5x API call to 5 different API). That makes Tokopedia Lite faster and more
efficient.

*****

### Cache

In some cases, not all queries need to call other APIs to get data. In
Tokopedia, we have API to provide data of product categories in our marketplace.
Because this data is not frequently updated, so we decided to cache it in our
GraphQL server.

<span class="figcaption_hack">Query Category</span>

Every query for *mainCategoriesQueries* will resolve with checking our cache
first. If cached data exists, GraphQL will immediately return the value from
cache. The question is, how do we do that? Actually we only use
[redis](https://redis.io/) as our cache server

![](https://cdn-images-1.medium.com/max/1600/1*i1d88Q8NNrRv6kjf7Ssw4g.png)
<span class="figcaption_hack">Redis</span>

![](https://cdn-images-1.medium.com/max/1600/1*N51cfUvAoePGy_moJoZbhQ.jpeg)
<span class="figcaption_hack">Cache Mechanism</span>

*****

We have many amazing and untold stories inside Tokopedia. We are always willing
to try different methods to satisfy our customers. Have any suggestion for us to
take it to the next level? Feel free to write in comments or you can [join
us](http://tokopedia.com/careers)! Please check out our [careers
page](http://tokopedia.com/careers) for more information.

* [React](https://medium.com/tag/react?source=post)
* [GraphQL](https://medium.com/tag/graphql?source=post)
* [Tokopedia](https://medium.com/tag/tokopedia?source=post)