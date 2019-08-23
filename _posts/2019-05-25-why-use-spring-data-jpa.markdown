---
layout: post
title:  "Why use Spring data JPA ?"
date:   2019-05-25 13:55:23 +0530
categories: Java
---

# Why use Spring data JPA ?

In this blog, I am going to discuss about one of the newest and finest additions in the Spring group of projects which is Spring data jpa. For the uninitiated, the main advantage that it brings to the table is that it helps in reducing boiler plate JDBC code to a great extent and thereby it keeps codebase clean.

So what really is Spring data JPA ? Do we still need a JPA implementation like Hibernate / EclipseLink when we are using Spring data jpa.
The answer to the last question is yes - we indeed still need a JPA implementation (like Hibernate) when we are using Spring data JPA. 

Spring data JPA is **NOT an alternate** to Hibernate - we still need a JPA implementation like Hibernate. But our basic boiler plate code for a CRUD functionality is drastically reduced if we spring data JPA.

Let us see with a small example taken from my Github project [SpringDataJPAWithoutBoot](https://github.com/msoumik78/springDataJpaWithoutSpringBoot) for this. Below are the steps required to create a spring-data jpa based project:
* First create the JPA entity class with Lombok annotation for getter and setter:
{% highlight ruby %}

@Getter
@Setter
@ToString
@Entity
public class Customer {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;
	private String firstName;
	private String lastName;
	private int age;
	private double monthlySalary;
	private String country;
	private String language;
}

{% endhighlight %}

* Create a repository interface by extending the CRUDRepository interface:
{% highlight ruby %}

public interface CustomerRepository extends CrudRepository<Customer, Long> {
}
{% endhighlight %}
* With this much code - it is ready to execute basic CRUD commands. Let us see the code snippets from the service layer 
{% highlight ruby %}
public class CustomerService {
	@Autowired
	private CustomerRepository customerRepository;

	public void addCustomer(Customer customer){
		customerRepository.save(customer);
	}

{% endhighlight %}
* So with this, our code is ready to at least invoke the basic CRUD methods (findAll, delete, save ) and without any boilerplata code.
* What is even more interesting is that with more change requests focussing on this project, we can 
{% highlight ruby %}
public interface CustomerRepository extends CrudRepository<Customer, Long> {
	List<Customer> findByLastName(String lastName);

	List<Customer> findByCountryAndLanguage(String country, String language);

	List<Customer> findByAgeGreaterThan(int age);
}
{% endhighlight %}

A couple of interesting things to note here:
* As long as we follow simple naming convention, we really do not need to right any boiler plate code for queries
* The code is very clean and without any clutter which is normally the case only when we develop completely in house
