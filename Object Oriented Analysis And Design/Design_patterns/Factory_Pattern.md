The Factory pattern provides a way to use an instance as a objectfactory.
The factory can return an instance of one of several possible classes (in a
subclass hierarchy), depending on the data provided to it.

 **Where to use**

- When a class can't anticipate which kind of class of object it must create.
- You want to localize the knowledge of which class gets created.
- When you have classes that is derived from the same subclasses, or they
	may in fact be unrelated classes that just share the same interface. Either
	way, the methods in these class instances are the same and can be used
	interchangeably.
- When you want to insulate the client from the actual type that is being
	instantiated.


**Benefits:**
- The client does not need to know every subclass of objects it must create. It only needs one reference to the abstract class/interface and the factory object.
- The factory encapsulates the creation of objects. This can be useful if the creation process is very complex.

**Drawbacks/consequences:**
- There is no way to change an implementing class without a recompile.

```
             +-------------------+
             |   Abstract        |
             |   Product         |<========+--------------+
			 +-------------------+     	   | Concrete     |
										   | Factory      |
				                           +=-------------+
                 ^        ^                        ^
                 |        |                        |
                 |        |                        |
                 |        |                +--------------+
                 |        |                |  Client      |
                 |        |                +--------------+
                 |        |
                 |        |
+----------------|        |-------------------+
|   Concrete     |        |   Concrete        |
|   ProductA     |        |   ProductB        |
+----------------|        |-------------------+

```



**Small example**
This example shows how two different concrete Products are created using
the ProductFactory. ProductA uses the superclass writeName method.
ProductB implements writeName that reverses the name.

```java
public abstract class Product {
public void writeName(String name) {

System.out.println("My name is "+name);
	}
}

public class ProductA extends Product { }


public class ProductB extends Product {

	public void writeName(String name) {
	StringBuilder tempName = new StringBuilder().append(name);
		System.out.println("My reversed name is" +
		tempName.reverse());
	}
}

public class ProductFactory {

	Product createProduct(String type) {
		if(type.equals("B"))
			return new ProductB();
		else
			return new ProductA();
	}
}

public class TestClientFactory {
	public static void main(String[] args) {
		ProductFactory pf = new ProductFactory();
		Product prod;
		prod = pf.createProduct("A");
		prod.writeName("John Doe");
		prod = pf.createProduct("B");
		prod.writeName("John Doe");
	}
}
```
```bash
My name is John Doe
My reversed name is eoD nhoJ

```

**Usage example**
```java
import java.sql.*;

public class TestClientFactoryUsage {
	static Connection con;
	static Statement stmt;
	public static void main(String[] args) {
		try {
			Class.forName("oracle.jdbc.driver.OracleDriver");
				con = DriverManager.getConnection("myServer", "user",
"password");
				stmt = con.createStatement();
		} catch(Exception e) {}
}
}
```