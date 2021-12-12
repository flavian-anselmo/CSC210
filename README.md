# CSC210-OOP2-LAB-REPORT
## Scenario of scaiproduction
ScaiProduction Ltd are specialists in producing production line manufacturing
plants. They could be asked to create a production plant for any type of product
ranging from a simple packaging system to a variety of electronic devices.
Recently they have been asked to create a production line for multimedia
devices which include music and movie players. They wish to employee you to
design a template in Java for creating and recording all future production line
items. For this particular production facility you will only implement a concrete
class for music and movie players. Your task is to create a flexible structure that
could be used in any production line. This structure would then allow easy
modification to handle different products.
## Step 1 
Created an interface called item with unimplemented methods and some attributes listed below in code snippets.
This is how the interface was written.

### Attributes or properties 
This was a static variable which is also a class variable 
```java
public final static String MANUFACTURER = "ScaiProduction";
```
### Methods 
All this methods will be used by any class that implements the interface Item.
All the getters  have a respective return types  while the setters have a void since they return nothing. 
```java
public void  setProductionNumber(int productionNumber);  //set the production number if needed 

public void  setName(String name);                       //set the name of the product 

public String getName();                                 //get the name of the product 

public Date getManufacturingDate();                      //get the exact manufacturing date 

public int getSerialNumber();                            //get the product serial number 
```
## Step 2 
Task 2 was all about creating enums. Enums are a specification for a class where all instances of the class are created within the class 
Enums are datatypes that contain a fixed set constants for our case we have some ItemTypes that will store some information. The type has its name and its code.This Enum ItemType was implemented as shown below.
```java
public enum ItemType  {
  
  Audio("AU"),
  Visual("VI"),
  AudioMobile("AM"),
  VisualMobile("VM");

  private String code;
  ItemType (String code ){
    this.code = code;
  }
  public String getCode(){
    return code ;
  }
}
```
Made it public since the enum will be accessed with other classes during instantiation of objects when creating a product. 
## Step 3 
Created an abstract class called ```Product``` which implemeted the interface ```Item``` This means that all the methods defined in ```Item``` had full implementaions.The methods from interface ```Item``` were ***overriden*** Below are code snippets to the method implementations.  
```java 
@Override
public void setProductionNumber(int productionNumber){
	this.serialNumber=productionNumber;
		
}
@Override
public void setName(String name ){
	this.name=name;
}
	
@Override
public String getName(){
	return this.name;
}

@Override
public Date getManufacturingDate(){
	return this.manufacturedOn;
}

@Override
public int getSerialNumber(){
	return this.serialNumber;
}
```
Other fields were added to the ```Product``` class.THey are listed in the code snippet below.They have respective data types as stated in the problem statement.
```java
public int serialNumber;
public String manufacturer;
public Date manufacturedOn;
public String name;
```
An static variable of type ```int``` was created to track any product that is being made.The initial value of the class variable was set to one 
then incremented any time an object is instantiated or created.
```java
static int  currentProductionNumber=1;
```
A constractor was created that will help during object instantiation.Serialnumber incremented was done in the constactor to allow automatic increament.
```java 
public Product(String name){
	this.name = name;
	this.manufacturer=Item.MANUFACTURER;
	serialNumber=currentProductionNumber++;
	manufacturedOn= new Date();
}
```
```this.manufacturer``` was initialised to ```Item.MANUFACTURER``` which is a static variable in the interface ```Item```
```serialNumber was initalised to ```currentproductionNumber++``` whic is an increment 
```manufaturedOn``` was initialised to new Date()``` whch used a package that was imported.\
The packeges imported are:
- import java.util.Date;
- import java.util.List;\
A ```toString``` method was added to return the product details as a Sring in a certain format stated in the problem statement.\
\
	 Manufacturer: ScaiProduction\
	 Serial Number : 1\
	 Date: Wed 8 DEC. 08:10:43 BST 2021\
	 Name: piper-chat\
	 
	 Below is a code snippet to the toString() method.\
	 
	 
	 
```java
public String toString() {
   return "Manufacturer: "+this.manufacturer+"\n" + "SerialNumber: "+serialNumber+"\n"+"Date: "+manufacturedOn+"\n"+"Name: "+this.name;
}	
```
## Step 4
## Step 5
## Step 6 
## Step 7 
## Step 8 
## Step 9
## Step 10
## Step 11 
## Step 12
## Step 13
## Step 14 
## Step 15 
## Step 16





