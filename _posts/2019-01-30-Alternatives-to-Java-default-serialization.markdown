|layout|title|date|categories|
|---|---|---|---|
post|"Alternatives to Java's default serialization"|2019-01-30 16:55:23 +0530|jekyll update| 

### Alternatives to Java's default Serialization
I have already discussed in one of my past blogs on how implementing default serialization in Java is a just a breeze. We just need to implement a marker interface and then the JVM does all the magic of serialization in the background. But this comes at a significant performance cost.
Hence this blog looks at the different alternatives to Java's default serialization.

#### Implementing Serializable interface but overriding the readObject and writeObject methods
Although Serializable is a marker interface, still one can have some degree of control by implementing the writeObject() and readObject() methods and these methods are indeed called by JVM pre-serialization and de-serialization respectively.

Following are some code snippets below:
{% highlight ruby %}
  private void readObject(ObjectInputStream aInputStream) throws ClassNotFoundException, IOException
    {      
        firstName = aInputStream.readUTF();
        lastName = aInputStream.readUTF();
        accountNumber = aInputStream.readInt();
       }
 
    private void writeObject(ObjectOutputStream aOutputStream) throws IOException
    {
        aOutputStream.writeUTF(firstName);
        aOutputStream.writeUTF(lastName);
        aOutputStream.writeInt(accountNumber);
     }
{% endhighlight %}

#### Implementing Externalizable interface
This is another alternative approach of customizing the java serialization process. First step is to implement the Externalizable interface (this is not a marker interface and hence you need to implement the writeExternal and readExternal methods )

Following are some code snippets below:
{% highlight ruby %}
  @Override
    public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
	name 	= (String) in.readObject();
	salary  = in.readInt();
    }

    @Override
    public void writeExternal(ObjectOutput out) throws IOException {
	out.writeObject(name);
	out.writeInt(salary);
    }
{% endhighlight %}

#### Hadoop Serialization

#### AVRO Serialization


#### Protobuf Serialization


### Some final thoughts 
