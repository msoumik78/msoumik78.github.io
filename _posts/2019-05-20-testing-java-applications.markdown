---
layout: post
title:  "Testing Java applications"
date:   2019-05-20 13:55:23 +0530
categories: Java
---

# Java application testing methodologies
There are several levels of testing that are progressively executed on a production ready java applications. These several roiunds of testing test different aspects of the application and this blog discusses about these various levels of testing and their purposes.

* **Unit testing** - This is the first and basic testing where every single java method is tested. This testing is actually a "white box testing" and is done using mocking frameworks (Mockito, PowerMock etc.)

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
* Verification at the end, for the first case - it should confirm that DAO layer is not called and for the second case it is confirmed that the DAO layer is called once (*doNothing ensures that nothing happens on the mock object when the DAO layer method is called*) 

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
		
		public boolean testSaveCustomer_whenCustomerIsValid() {
			doNothing().when(customerDAO.save(customer));
			customerService.saveCustomer(customer);
			verify(customerDAO.times(1)).save();
		}				
	}
{% endhighlight %}



* **Integration testing** - This is the second level of testing where several layers of the application are tested in one shot. So if we look at the previous example, for integration testing, mocks are never created. 
Some aspects of integration testing are as follows:
* Nothing is mocked
* the application is tested almost end to end - hence you will see in the below example that the DAO layer is instantiated and not tested. Often in IT tests

{% highlight ruby %}
	public class ITTestCustomerService {
		
		public boolean testSaveCustomer_whenCustomerIsValid() {
			CustomerDAO customerDAO = new CustomerDAO();
			Customer cutomer = new Customer ();
			customer.build.firestName("Soumik").lastName("Mukherjee").profession("Java Architect");
			boolean result = customerService.saveCustomer(customer);
			assertTrue(result);
		}	
		
		public boolean testSaveCustomer_whenCustomerAlreadyExists () {
			CustomerDAO customerDAO = new CustomerDAO();
			Customer cutomer = new Customer ();
			customer.build.firestName("Soumik").lastName("Mukherjee").profession("Java Architect");
			boolean result = customerService.saveCustomer(customer);
			assertFalse(result);
		}			
		
	}
{% endhighlight %}


* **Functional testing** - This is the last and final level of testing where the application is tested end-to-end (usuually from the UI perspective) and 
using some UI testing automation tool (like Selenium)

