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
Created an interface called item with unimplemented methods and some attributes listed below 

### Attributes or properties 
This was a static variable which is also a class variable 
```java
public final static String MANUFACTURER = "ScaiProduction";
```
### Methods 
All this methods will be used by any class that implements the interface Item 
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




## Step 3 
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





