|layout|title|date|categories|
|---|---|---|---|
post|"Java's default serialization"|2017-08-22 16:55:23 +0530|Java| 

### Serialization

Serialization is the process of converting in-memory objects to bytestream for either storing the data in persistent storage (like filesystem) or passing the data across network (as in RPC calls). De-serialization is the reverse process of converting the bytestream back to Java in-memory objects. Serialization / De-serialization is frequently involved in distributed computing technologies like RMI , EJB and nowadays in Hadoop eco system. This blog discusses about Java's default serialization and its limitations and then I have another blog which discusses the alternative options to Java's default serialization. 

#### Java's default serialization
One can mark an object to be serializable just by just implementing the *marker* Serializable interface. That's it and the developer does not need to do anything else! This single declaration will ensure that Java's default serialization will kick in once you want to serialize the object. 

Following is some code snippet for Java's default serializatiopn technique:
{% highlight ruby %}

// Serialization (Converting an in-memory object to serialized state) -  
// This assumes that Object1's class implements Serializable interface
ObjectOutputStream os = new ObjectOutputStream (new FileOutputStream("x.ser")); 
os.writeObject(Object1);

// De-Serialization (Converting a serialized state to in-memory object) -   
ObjectInputStream os = new ObjectInputStream (new FileInputStream("x.ser")); 
os.readObject();

{% endhighlight %}

Following are some salient aspects of Java's default serialization: 
* Note that **static** & **transient** variables are not serialized. One can mark a variable **transient** if that variable does not contain any original value (i.e. it is calculated from other fields)
* When an object gets serialized - the entire object graph gets serialized which means that all objects referenced by the object gets serialized. If any object in the graph is not serializable - the entire chain breaks and serialization fails. Hence Serialization is a *whole or none proposition.* During the process of de-serialization, constructors are not called (and hence the objects are not default initialized). If any object in the hierarchy is not serializable - constructor chaining starts from that point. Once constructor chaining starts, it can't be stopped.
* A long field by the name **"serialVersionUID"** can be used to prevent any issues during de-serialization process if there is a change in the class after serialization happened. (private long serialVersionUID). But using this field means that the programmer is taking risk of any bad changes.

Following are the acceptable changes for Serialization - 
* Field addition
* Fields changed from transient to non transient.      

Following are the un-acceptable changes for Serialization - 
* Field deletion 
* Fields changed from non transient to transient

Although implementing Java's default serialization is a breeze (by simply implementing one marker interface), following are several disadvantages of the default serialization:
*  Java's default serialization stores the metadata (class details) along with the serialized object to make it more generic based approach and hence the serialized data occupies much more space and its not suitable for RPC calls
*  Further Java's default serialization always creates a new object instance in memory during the process of de-serialization and this approach also might not be most memory efficient.

So these are some of the reasons for which one can consider alternatives to Java's default serialization. Will be discussed in another blog.
