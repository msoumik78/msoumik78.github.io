---
layout: post
title:  "GraphQL and why is it important"
date:   2021-02-05 13:55:23 +0530
categories: MicroServices
---

# GraphQL motivation

In this post, I am going to discuss the motivations of Graph QL and how to build a GraphQL based service using SpringBoot and Java/Kotlin.
Let us first understand why GraphQL exists and what problem does it solve. Well , we are all aware that REST services are now ubiquitous because of its very consistent resource based architecture.
But one of the problems or challenges of REST is that - if a frontend has to collate data from multiple resources, then it will have to call multiple REST endpoints in order to display the data in UI.
While these backend calls can be made parallel and async in some cases - but in majority of cases, these calls have to be done sequential because of the inter-dependency of the resources required.
And this causes a huge performance problem in some cases.

GraphQL is an alternate approach in which the backend can be queried based on the data required by frontend and hence the entire data model can be pulled in a single remote call.
This approach was first used by Facebook and it is gaining popularity at many places.


Below are the steps you can follow to build a simple but effective Spring boot based graphQL solution:
- First import the following dependencies dependencies in your pom. Essentially, they bootstrap a servlet which receives all the graphql invocations.
{% highlight ruby %}
		<dependency>
			<groupId>com.graphql-java</groupId>
			<artifactId>graphql-spring-boot-starter</artifactId>
			<version>5.0.2</version>
		</dependency>
		<dependency>
			<groupId>com.graphql-java</groupId>
			<artifactId>graphql-java-tools</artifactId>
			<version>5.2.4</version>
		</dependency>
{% endhighlight %}
- In the GraphQL world, we broadly consider the following types:
  - type entity -> this corresponds to the actual resource
  - type Query -> this is equivalent to a select query on one or multiple entities
  - type Mutation --> this is equivalent to an insert / update query on one or multiple entities
  Ususally, they are defined a file which has the extension .graphqls

- Create the entities corresponding to the database tables that will be involved
- Create a Resolver layer, where you will implement the GraphQLQueryResolver and GraphQLResolver interfaces respectively.
  This is basically the service layer, in which you need to implement the logic of fetching/inserting corresponding to the query and mutations declared in the .graphqls files.
  This should use the DAO layer and ideally use SPring Data JPA and fetch / insert from / to the database.
  Some snippets below :
{% highlight ruby %}  
  public class Query implements GraphQLQueryResolver {
      public long countAuthors() {
        return authorRepository.count();
    }
    public Iterable<Author> findAllAuthors() {
        return authorRepository.findAll();
    }
  }
  
  public class Mutation implements GraphQLMutationResolver {
      // Saving in multiple entities
      public Tutorial createTutorial(String title, String description, Long authorId) {
        Tutorial book = new Tutorial();
        book.setAuthor(new Author(authorId));
        book.setTitle(title);
        book.setDescription(description);
        tutorialRepository.save(book);
        return book;
    }
  }
{% endhighlight %}


# Final thoughts - should we use REST or embrace GraphQL ?
Well there is no easy answer. In most cases, REST would be probably the best choice because of architecural consistency. However, if there are serious concerns about latency, a GraphQL solution can be considered..
In general, there can be 2 strategies if you decide to implement GraphQL:
- If it is a Greenfield project and the UI nature is such that it requires data to be pulled across multiple REST resources, then don't build REST styled services, rather build GraphQL services from scratch.
- If it is a Greenfield project but the UI can be satisfied by pulling data from max 2 to 3 resources, go for standard REST styled resources.
- If some REST services already exist but still the latency is high for some UIs because it has to call multiple REST endpoints, then a hybrid approach can be built, when a REST 

