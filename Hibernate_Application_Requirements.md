Any hibernate application must always contains 4 files totally.

* POJO class
* Mapping XML
* Configuration XML
* One java file to write our logic

Actually these are the minimum requirement to run any hibernate application, and in fact we may require any number of POJO classes and any number of mapping xml files (Number of POJO classes = that many number of mapping xmls), and only one configuration xml and finally one java file to write our logic.
### POJO Class:
* POJO is a simple java file, no need to extend any class or implement any interface.
* This POJO class contain private properties variables, and for each property a setter and a getter

```java
public class  Java4s
{
private int stNo;
private String stName;
private String stAddress;

     public void setStno(int stNo)
     {
     this.stNo=stNo;
     }
     public int getStNo()
     {
     return stNo;
     }

     public void setStName(int stName)
     {
     this.stName=stName;
     }
     public String getStName()
     {
     return stName;
     }

     public void setStAddress(String stAddress)
     {
     this.stAddress=stAddress;
     }
     public String getStAddress()
     {
     return stAddress;
     }

}
```

## Mapping xml For POJO:
Here is the mapping file related to above pojo class.

```java
<hibernate-mapping>
   <class name="Java4s" table="STable">
         <id name="stNo" column="SNo">
              <generator class="assigned"/>
         </id>
         <property name="stName" column="SName" />
         <property name="stAddress "/> </class>
</hibernate-mapping>
```
Yes., see in this above mapping xml, for stAddress property i have not written any column name i just been specified  <property name=”stAddress “/>, this means in the database the column name for stAddress property will also be stAddress, in these cases we can ignore the column attribute to write.

## Configuration XML

```java
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE hibernate-configuration PUBLIC
"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
"http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
<session-factory“>

<!-- Related to the connection START -->
<property name="connection.driver_class">oracle.jdbc.driver.OracleDriver
</property>
<property name="connection.url">jdbc:oracle:thin:@www.java4s.com:1521:XE</property>
<property name="connection.user">user</property>
<property name="connection.password">password</property>
<!-- Related to the connection END -->

<!-- Related to hibernate properties START -->
<property name="show_sql">true</property>
<property name="dialet">org.hibernate.dialect.OracleDialect</property>
<property name="hbm2ddl.auto">update</property>
<!-- Related to hibernate properties END -->

<!-- Related to mapping START -->
<mapping resource="Our mapping xml file name" />
<!-- Related to the mapping END -->

</session-factory>
</hibernate-configuration>
```
