---
layout: post
title:  "Testing Java applications"
date:   2019-05-20 13:55:23 +0530
categories: Java
---

# Java application testing methodologies
There are several levels of testing that are progressively executed on production ready java applications. These several rounds of testing test different aspects of the application and this blog discusses about these various levels of testing and their purposes.

* **Unit testing** - This is the first and basic testing where every single java method is tested. This testing is basically a "white box testing" and is done using mocking frameworks (Mockito, PowerMock etc.)

Below is an example of a sample Service layer class in which the DAO layer class is injected.
{% highlight ruby %}
	public class CustomerService {
		
		@Resource
		private CustomerDAO customerDAO;
	
		public boolean saveCustomer(Customer customerDAO) {
			if (null != customer) return false;
			return customerDAO.save(customer);
		}	
	}
{% endhighlight %}


Below is an example of how the class has been unit tested, a few points to note here:
* Creation of mock object of the DAO layer - mock objects are just dummy objects
* 2 different test cases corresponding to one where passed customer object is null and other where it is not null
* Verification at the end. For the first case - it should confirm that DAO layer is not called and for the second case it is confirmed that the DAO layer is indeed called once (*doNothing ensures that nothing happens on the mock object when the DAO layer method is called*) 

{% highlight ruby %}
	@RunWith(MockitoJUnitRunner.class)
	public class TestCustomerService {
		
		@InjectMocks
		private CustomerService customerService;
		
		@Mock
		private CustomerDAO customerDAO;
		
		@Mock
		private Customer customer;
	
		@Test
		public boolean testSaveCustomer_whenCustomerIsNull() {
			Customer cust = null;
			customerService.saveCustomer(cust);
			verify(customerDAO.times(0)).save();
		}	
		
		@Test
		public boolean testSaveCustomer_whenCustomerIsValid() {
			doNothing().when(customerDAO.save(customer));
			customerService.saveCustomer(customer);
			verify(customerDAO.times(1)).save();
		}				
	}
{% endhighlight %}


* **Integration testing** - This is the second level of testing where several layers of the application are tested in one shot. So if we look at the previous example, for integration testing, mocks are never created. 

Below is an example where the same class is now subjected to integration testing but before you see the below code - please review the below interesting features:
* Nothing is mocked in this case 
* the application is tested almost end to end - hence you will see in the below example that the DAO layer is actually instantiated and record is inserted during test. And finally its verified from the database (in method *checkIfCustomerIsInsertedInDB*) if the record has been actually inserted.
{% highlight ruby %}
	public class ITTestCustomerService {
		
		@Test
		public boolean testSaveCustomer_whenCustomerIsValid() {
			CustomerDAO customerDAO = new CustomerDAO();
			Customer customer = new Customer ();
			customer.build.firestName("Soumik").lastName("Mukherjee").profession("Java Architect");
			customerService.saveCustomer(customer);
			assertTrue(checkIfCustomerIsInsertedInDB(checkIfCustomerIsInsertedInDB));
		}	
		
		@Test
		public boolean testSaveCustomer_whenCustomerAlreadyExists () {
			CustomerDAO customerDAO = new CustomerDAO();
			Customer customer = new Customer ();
			customer.build.firestName("Soumik").lastName("Mukherjee").profession("Java Architect");
			boolean result = customerService.saveCustomer(customer);
			assertFalse(checkIfCustomerIsInsertedInDB(checkIfCustomerIsInsertedInDB));
		}		
		
		private boolean checkIfCustomerIsInsertedInDB(Customer customer){
		..........
		// logic to go in DB and check whether the customer is inserted
		}
		
	}
{% endhighlight %}


* **Functional testing** - This is the last and final level of testing where the application is tested end-to-end (usuually from the UI perspective) and using some UI testing automation tool (like Selenium). This is almost a complete blackbox testing when an UI automation tool (like Selenium) provides some values based on which the backend is called. Finally the values returned by the backend are verified again on the screen. So this is not an API testing but a complete functional testing.


* **Non functional Testing** - There are various types of **NON FUNCTIONAL** testing which are also carried out before pushing an application to production and following are the main types (I'll try to write a seperate blog post on non functional testing) : 

* Security / Penetration testing - This is done to find out if there are security issues (like HTML injection, SQL injection etc.) in the application.
* Latency testing - This testing tries to find out the average response times of each APIs under an optimum load.
* Throughput testing - This testing tries to find out the optimum number of parallel users the system can support without degrading the performance and within the given hardware capacity (Now this brings us to another interesting topic which is how to make horizontally scalable application).


