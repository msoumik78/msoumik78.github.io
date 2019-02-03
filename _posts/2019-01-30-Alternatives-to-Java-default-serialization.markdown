|layout|title|date|categories|
|---|---|---|---|
post|"Java's default serialization"|2019-01-30 16:55:23 +0530|jekyll update| 

### Alternatives to Java's default Serialization

Serialization is the process of converting in-memory objects to bytestream for either storing the data in persistent storage (like filesystem) or passing the data across network (as in RPC calls). De-serialization is the reverse process of converting the bytestream back to Java in-memory objects. Serialization / De-serialization is frequently involved in distributed computing technologies like RMI , EJB and nowadays in Hadoop eco system. This blog discusses about various ways in which one can attempt serialization/ de-serialization. 

#### Implementing Externalizable interface


#### Hadoop Serialization
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

#### AVRO Serialization


#### Protobuf Serialization


### Some final thoughts 
