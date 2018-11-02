## Hibernate Architecture:
The following diagram summarizes the main building blocks in hibernate architecture.

<p align="center"> 
<img src="https://cdn1.howtodoinjava.com/wp-content/uploads/2013/02/Hibernate-Architecture.png">
</p>

Let’s understand what each block represents.

### Configuration :
Generally written in hibernate.properties or hibernate.cfg.xml files.
Configuration is the file loaded into an hibernate application when working with hibernate, this configuration file contains 3 types of information..

* Connection Properties
* Hibernate Properties
* Mapping file name(s)

We must create one configuration file for each database we are going to use, suppose if we want to connect with 2 databases, like Oracle, MySql, then we must create 2 configuration files.

```java
<hibernate-configuration>
<session-factory>

<!-- Related to the connection START -->
<property name="connection.driver_class">Driver Class Name </property>
<property name="connection.url">URL </property>
<property name="connection.user">user </property>
<property name="connection.password">password</property>
<!-- Related to the connection END -->

<!-- Related to hibernate properties START -->
<property name="show_sql">true/false</property>
<property name="dialet">Database dialet class</property>
<property name="hbm2ddl.auto">create/update or what ever</property>
<!-- Related to hibernate properties END-->

<!-- Related to mapping START-->
<mapping resource="hbm file 1 name .xml" / >
<mapping resource="hbm file 2 name .xml" / >
<!-- Related to the mapping END -->

</session-factory>
</hibernate-configuration>
```
## Mapping:
* Mapping file is the heart of hibernate application.
* Every ORM tool needs this mapping, mapping is the mechanism of placing an object properties into column’s of a table.
* Mapping can be given to an ORM tool either in the form of an XML or in the form of the annotations.
* The mapping file contains mapping from a pojo class name to a table name and pojo class variable names to table column names.
While writing an hibernate application, we can construct one or more mapping files, mean a hibernate application can contain any number of  mapping files.
generally an object contains 3 properties like

* Identity (Object Name)
* State (Object values)
* Behavior (Object Methods)

But while storing an object into the database, we need to store only the values(State) right ? but how to avoid identity, behavior.. its not possible. In order to inform what value of an object has to be stored in what column of the table, will be taking care by the mapping,  actually mapping can be done using 2 ways,

* XML
* Annotations

```java
<hibernate-mapping>

<class name="POJO class name" table="table name in database">
<id name="variable name" column="column name in database" type="java/hibernate type" />
<property name="variable1 name" column="column name in database" type="java/hibernate type" />
<property name="variable2 name" column="column name in database" type="java/hibernate type" />
</class>

</hibernate-mapping>
```
