# 1. Spring Framework Course Overview.
![alt text](image.png)![alt text](image-1.png)
### Web related terms such as Html,Css,Js bootstraps etc.
![alt text](image-2.png)![alt text](image-3.png)
# 2. What is Spring Framework | Dependency Injection | Inversion of Control | Spring Core Module
![alt text](image-4.png)![alt text](image-5.png)![alt text](image-6.png)
- Kal Geeta ke jagah yadi bablu ka object ki requirement hue Ram ko
    - So pure code mein jaha jaha Geeta ka object hai wo replace karna honga bablu ke object se.
- So basically every time we have to change code and compile it again.

![alt text](image-7.png)
- kal yadi Geeta ka jaagah bablu ka object chaiye ramu ko
    - to Spring uska bhi object create karke de denga.
    - isme aapko code ko bar bar compile nhi karna padenga.

![alt text](image-8.png)![alt text](image-9.png)![alt text](image-10.png)
# 3. Overview of Spring Framework module.
![alt text](image-11.png)
### Spring Core:
- Consist of 4 module namely Core, beans, context,spel.
- Core & beans provide basic thing like dependency injection and IOC.
    - iske wajah se hi hum dependency inject kar sakte 
    - constructor/ setter injection all stuff.
- Context provide event propagation,resource loading, transperent creation of context, internationalization.
- Spel  abbreviate as expression language 
    - With this we can query or manipulate object graph at runtime.
### AOP
- Consist of 3 module namely Aspect, Instrumentation and messaging.
- Aspect provide method interceptors(method ke pehle ya baadme koyi kaam karna ho) & pointcuts(jisse hum code ko decouple kar pave.)
- messaging aap baanane ke liye use hota hai.
### Data Integration layer.
- Object Realtional Mapping
- Object Xml mapping.
- Orm ye ek integration layer provide karta hai.
    - yadi aapko hibernate apne application mein use karna raha so ye layer se possible ho jata.
### Web module
- web oriented feature provide karta.
### Test module
- Unit testing like JUNIT and mokito.
# 4. Spring IOC container.
![alt text](image-12.png)
- Spring ke sath hume ek component/container milta hai, jise hum Spring IOC  container kehte hai.
- It is responsible for.
    - Basically ye object ko create karta.
    - hold that object in memory
    - whenever require ye inject karta dependency.
- Basically it manage the life cyle object.
#### So spring container is a predefined program which manage the life cyle of object.
![alt text](image-13.png)![alt text](image-14.png)
# 5. Ways of Injecting dependency.
![alt text](image-15.png)
- As per above dig, Student class depend hai Address class ke object ke upar
- So IOC container sabse pehele Address class ki sari value set/intitialize  karke uska object create Karenga.
- Phir Student class ka object create karte hue, uski  id aur name initialize karenge and Address class ki object inject Karenga Student class attribute address mein.
- is tarah se student class ka bean i.e object create honga. Jise hum use kar sakte hai.

![alt text](image-16.png)![alt text](image-17.png)
- For Setter Injection
    - aapko apne class mein Setter methods define karni hongi.
- Object create karte waqt container call karenga setter methods.
    - Address class ka object create karte waqt container uski setter method call karke sari value initialize kar lenga.
- Similarly Student object create karte waqt IOC container call karenga setter method but jab setAddreess() method call karenga so waha IOC container Address class ki dependency inject kar denga.

![alt text](image-18.png)
- Constructor injection ke liye aapko class mein constructor likhna  honga.
- Object create  karte waqt IOC Conatiner constructor call karenga instead of setter method.
    
![alt text](image-19.png)![alt text](image-20.png)![alt text](image-21.png)![alt text](image-22.png)
# 6. Practical
![alt text](image-23.png)
### 1) Create a maven project
![alt text](image-24.png)![alt text](image-25.png)![alt text](image-26.png)![alt text](image-27.png)
### 2) Adding dependencies
##### spring core and context we require.
![alt text](image-29.png)
##### If you encounter with error then update the project
![alt text](image-30.png)
- Right Clk -> maven -> update project
##### U can also update java 
![alt text](image-31.png)![alt text](image-32.png)![alt text](image-33.png)![alt text](image-34.png)![alt text](image-35.png)
### 3) Creating beans
![alt text](image-36.png)
- create fileds with Constructor default + parameterized then Getter & setters then toString() method.
### 4) Creating configuration file & 5) Setter Injection
###### Create xml file - New then other
![alt text](image-37.png)![alt text](image-38.png)![alt text](image-39.png)![alt text](image-40.png)![alt text](image-41.png)
- Add dtd beans,context and p schema.

##### Pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.adi.springcore</groupId>
	<artifactId>springcore</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>springcore</name>
	<url>http://maven.apache.org</url>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	</properties>

	<dependencies>

		<!-- https://mvnrepository.com/artifact/org.springframework/spring-core -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-core</artifactId>
			<version>6.1.0</version>
		</dependency>

		<!--
		https://mvnrepository.com/artifact/org.springframework/spring-context -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
			<version>6.1.0</version>
		</dependency>

		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>3.8.1</version>
			<scope>test</scope>
		</dependency>
	</dependencies>
</project>
```
##### Student Pojo
```java
package com.adi.springcore;

public class Student {

	private String studentId;
	private String studentName;
	private String studentAddress;

	public Student() {
		super();
		// TODO Auto-generated constructor stub
	}

	public Student(String studentId, String studentName, String studentAddress) {
		super();
		this.studentId = studentId;
		this.studentName = studentName;
		this.studentAddress = studentAddress;
	}

	public String getStudentId() {
		return studentId;
	}

	public void setStudentId(String studentId) {
		System.out.println("Setter injection is getting called for id");
		this.studentId = studentId;
	}

	public String getStudentName() {
		return studentName;
	}

	public void setStudentName(String studentName) {
		System.out.println("Setter injection is getting called for name" );
		this.studentName = studentName;
	}

	public String getStudentAddress() {		
		return studentAddress;
	}

	public void setStudentAddress(String studentAddress) {
		System.out.println("Setter injection is getting called for address");
		this.studentAddress = studentAddress;
	}

	@Override
	public String toString() {
		return "Student [studentId=" + studentId + ", studentName=" + studentName + ", studentAddress=" + studentAddress
				+ "]";
	}

}
```
##### config.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>     
   <beans xmlns="http://www.springframework.org/schema/beans"     
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
   xmlns:context="http://www.springframework.org/schema/context"
   xmlns:p="http://www.springframework.org/schema/p" 
   xsi:schemaLocation="http://www.springframework.org/schema/beans 
   http://www.springframework.org/schema/beans/spring-beans.xsd
    http://www.springframework.org/schema/context 
   http://www.springframework.org/schema/context/spring-context.xsd
   ">
     
     <!-- This is our bean 
      		here we add dtd of bean, context and pschema
      -->
     <bean class="com.adi.springcore.Student"  name="student1">
     	<property name="studentId">
     		<value>12334</value>
     	</property>
     	     	
     	<property name="studentName">
     		<value>Aditya Rathor</value>
     	</property>
     	     	
     	<property name="studentAddress">
     		<value>Nagpur</value>
     	</property>
     </bean>
     
 </beans>
```
### 6) Main class
##### App.java
```java
package com.adi.springcore;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

/**
 * Hello world!
 *
 */
public class App 
{
    public static void main( String[] args )
    {
    	System.out.println("Hello_world");
        ApplicationContext context = new ClassPathXmlApplicationContext("com/adi/springcore/config.xml");
        Student  student = (Student) context.getBean("student1");
        System.out.println(student);
    }
}
```
#### Ab yadi hume change karna hai name toh humko code compile karne ki jarurat nhi .. sirf config file mein change karo and run it kafi hai.
![alt text](image-42.png)![alt text](image-43.png)
# 7. Property injection using p schema and using value as an attribute.
### IN previous video we inject property via Value as Tag/element.
![alt text](image-44.png)
###  Inject Property via Value as an Attribute
![alt text](image-45.png)
### If you want to create another object then create another bean
![alt text](image-46.png)![alt text](image-47.png)
### Inejct Property via Value as an P Schema
![alt text](image-48.png)
# 8. How to inject collection types i.e List,Set,Map and Properties.
- In previous video we see, how ***primitive  data type** will be injected by setter or property injection
    - via Value as an element/tag
    - via value as an attribute
    - via value as p schema.

![alt text](image-49.png)
### How Collection data type will be inject by setter or property injection
#### For List
- List can contain duplicate element
- we use List tag for inserting vlaue in list
- for null we simply write null tag.

![alt text](image-50.png)
#### For Set
- Set does not allow duplicate element
- we use set tag for inserting value in Set

![alt text](image-51.png)
#### For Map
- We use Map tag for inserting value in Map
- Map is nothing but group of entries
- Inside entry we have key-value pair.

![alt text](image-52.png)
#### For Properties
- We use props tag for inserting value in Properties
- Inside Props tag we use prop tag to specify key
- And we specify value in body part

![alt text](image-53.png)
# 9. Practical
### Create a separate package and write your code there.
#### Emp.java
```java
package com.springcore.collections;

import java.util.List;
import java.util.Map;
import java.util.Set;

public class Emp {

	private String name;
	// Employee having multiple phone numbers
	private List<String> phones;
	// Employee have multiple address
	private Set<String> address;
	// Employee doing multiple courses having certain duration/price
	private Map<String, String> courses;

	public Emp(String name, List<String> phones, Set<String> address, Map<String, String> courses) {
		super();
		this.name = name;
		this.phones = phones;
		this.address = address;
		this.courses = courses;
	}

	public Emp() {
		super();
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public List<String> getPhones() {
		return phones;
	}

	public void setPhones(List<String> phones) {
		this.phones = phones;
	}

	public Set<String> getAddress() {
		return address;
	}

	public void setAddress(Set<String> address) {
		this.address = address;
	}

	public Map<String, String> getCourses() {
		return courses;
	}

	public void setCourses(Map<String, String> courses) {
		this.courses = courses;
	}

	@Override
	public String toString() {
		return "Emp [name=" + name + ", phones=" + phones + ", address=" + address + ", courses=" + courses + "]";
	}

	
}
```
#### configuration file
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns:context="http://www.springframework.org/schema/context"
	xmlns:p="http://www.springframework.org/schema/p"
	xsi:schemaLocation="http://www.springframework.org/schema/beans 
   http://www.springframework.org/schema/beans/spring-beans.xsd
    http://www.springframework.org/schema/context 
   http://www.springframework.org/schema/context/spring-context.xsd
   ">
   
	<bean class="com.springcore.collections.Emp" name="employee" >	
		<property name="name" value="Radhe" />
		
		<property name="phones">
			<list>
				<value>34343435</value>
				<value>121334</value>
				<null></null>
			</list>
		</property>
		
		<property name="address">
			<set>
				<value>Delhi</value>
				<value>Nagpur</value>
				<value>Ayodhya</value>
			</set>
		</property>
		
		<property name="courses">
			<map>
				<entry key="java" value="2months" />
				<entry key="Sql" value="1 months" />
			</map>
		</property>		
		
		
	</bean>
</beans>
```
#### Main app
```java
package com.springcore.collections;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class TestCollecitonInjection {

	public static void main(String[] args) {
		
		ApplicationContext context = new ClassPathXmlApplicationContext("com/springcore/collections/configCollection.xml");

		
		Emp emp1 = (Emp) context.getBean("employee");
		
		System.out.println(emp1);
		System.out.println("-------------");
		System.out.println("Name is :          "+ emp1.getName());
		System.out.println("List of phones : "+emp1.getPhones());
		System.out.println("Set of address : "+emp1.getAddress());
		System.out.println("Map of courses : "+emp1.getCourses());
	}

}
```
#### Output
```
Emp [name=Radhe, phones=[34343435, 121334, null], address=[Delhi, Nagpur, Ayodhya], courses={java=2months, Sql=1 months}]
-------------
Name is :          Radhe
List of phones : [34343435, 121334, null]
Set of address : [Delhi, Nagpur, Ayodhya]
Map of courses : {java=2months, Sql=1 months}
```
### Some modification 
#### If your list contain only 1 value, then you need not to provide explicitly list tag
![alt text](image-54.png)
#### If you require blank list
![alt text](image-55.png)
# 10. Injecting Refrence type 
![alt text](image-58.png)
### Injecting Ref as an element
![alt text](image-59.png)
### A.java
```java
package com.springcore.ref;

public class A {

	private int x;

	private B ob;

	public A() {
		super();
		// TODO Auto-generated constructor stub
	}

	public int getX() {
		return x;
	}

	public void setX(int x) {
		this.x = x;
	}

	public B getOb() {
		return ob;
	}

	public void setOb(B ob) {
		this.ob = ob;
	}

	@Override
	public String toString() {
		return "A [x=" + x + ", ob=" + ob + "]";
	}

}
```
### B.java
```java
package com.springcore.ref;

public class B {

	private int y;

	public B() {
		super();
		// TODO Auto-generated constructor stub
	}

	public int getY() {
		return y;
	}

	public void setY(int y) {
		this.y = y;
	}

	@Override
	public String toString() {
		return "B [y=" + y + "]";
	}

}
```
### configuration file
```xml
<?xml version="1.0" encoding="UTF-8"?>     
   <beans xmlns="http://www.springframework.org/schema/beans"     
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
   xmlns:context="http://www.springframework.org/schema/context"
   xmlns:p="http://www.springframework.org/schema/p" 
   xsi:schemaLocation="http://www.springframework.org/schema/beans 
   http://www.springframework.org/schema/beans/spring-beans.xsd
    http://www.springframework.org/schema/context 
   http://www.springframework.org/schema/context/spring-context.xsd
   ">
	
	<bean class="com.springcore.ref.B" name="bref" p:y="12" />	
	
	<bean class="com.springcore.ref.A" name="aref">
		<property name="x" value="20"/>
		<property name="ob">
			<ref bean="bref"/>
		</property>
	</bean>  
     
 </beans>
```
### main class
```java
package com.springcore.ref;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class TestRef {

	public static void main(String[] args) {

		ApplicationContext context = new 
				ClassPathXmlApplicationContext("com/springcore/ref/configRef.xml");

		A temp = (A) context.getBean("aref");

		System.out.println(temp);
		System.out.println("============");
		System.out.println("x value is : "+ temp.getX());
		System.out.println("y value is : "+ temp.getOb().getY());
	}

}
```
### Output
```
A [x=20, ob=B [y=12]]
============
x value is : 20
y value is : 12
```
### In previous example we use refrecne as an element
### Now we use Refrence as an attribute
![alt text](image-56.png)
### You can use Refrence via pschema
![alt text](image-57.png)
# 11. Constructor Injection



    

