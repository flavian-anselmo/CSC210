# CSC210-OOP2-LAB-REPORT
## Group Members
|id|Name   |Registration   |  
|---|---|---|
|0|Anselemo flavian   |  **COM/0039/20**  |  
|1| Brian Leposo   | **COM/0024/20**  |  
|2| Joy Nafula    |**COM/0059/20**   |   
<!-- |3| Cyrus Mwendwa   |**COM/0013/20**   |   
|4| Titus Shikomela   |**COM/0035/20**   |   
|5| Clinton Otieno    |**COM/0061/20**   |    -->

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
This was a short step where we created an Interface called ```MultimediaControl``` that will be responsible for providing 4 methods 
- ```play()```
- ```stop()```
- ```previous()```
- ```next()```\
Code snippet to the interface is shown below:
```java

public interface MultimediaControl {
   public void play();
   public void stop();
   public void previous();
   public void next();	
}
```
## Step 5
An ``AudioPlayer`` class was created\
This class implemented the ``MultiController`` interface and is a subclass of ``Product`` \
```java
public class Audioplayer extends Product implements MultimediaControl 
```
Two fields were added which are listed below with code snippets\

```java
public String audioSpecification;
public ItemType mediaType;
```
A constractor was created to be used during instatiation.The constractor inherited the ``name`` field from the Parent constractor \
Code Snippet:\
```java
public Audioplayer(String name,String audioSpecification) {
   super(name);
   this.audioSpecification = audioSpecification;
   this.mediaType=ItemType.Audio;
}

```
The methods from the ```MultiController``` interface were implemented as follows:\
Code Snippet:\
```java
@Override
public void play() {
		
	System.out.println("Play-Audio ");
}

@Override
public void stop() {
	System.out.println("Stop-Audio");
		
}

@Override
public void previous() {
	System.out.println("<<<<Previous");		
}

@Override
public void next() {
	System.out.println("Next>>>>");
		
}
```
Added a ``toString()`` method that uses another method from the parent class\
Code Snippet:
```java
public String toString(){
    return super.toString()+"AudioSpec: "+this.audioSpecification+"\n"+"AudioType: "+this.mediaType+"\n";
}
```

## Step 6 
Created a Driver class ``Driver_Audioplayer`` to test the functionality of the AudioPlayer\
A Driver class usually has a main function where excecution begins\
Tested the functionality by making a class instance ``audioplayer``..\
Example of the instance\
```java
Audioplayer audioPlayer=new Audioplayer("HeadShot", "HD");

```
Using the class instance we can now call the 4 methods \
The methods will be accessed as shown by the code snippets below\
```java
audioPlayer.play();
audioPlayer.next();
audioPlayer.stop();
audioPlayer.previous();
```
Code Snippet to the Driver class\
```java
public class Driver_Audioplayer {
  public static void main(String[] args) {
     Audioplayer audioPlayer = new Audioplayer("HeadShot", "HD");
     audioPlayer.play();
     audioPlayer.next();
     audioPlayer.stop();
     audioPlayer.previous();	
  }	
}

```
To print out the details of the audio player, We called the method ``toString()`` .\
Code snippet:
```java
System.out.println(audioPlayer.toString());
```

## Step 7 
The Production facility is also creating Movieplayer and since it will contain screens we created 2 different flavors of the screens\
This was done by the use of Enums``MovieType``  which was declared in the class ```Product``` . \
There are two types of screens for our scenario that is ``LCD``/ and ``LED``.\
Code snippet:
```java
public enum MovieType{
   LCD,
   LED;
}
```
## Step 8 
Created interface ``ScreenSpec`` as instracted from the problem statement\
The interface has 3 methods that will be implemeted by other classes \
The method declarations are:
```java
public String getResolution();
public int getRefreshRate();
public int getResponseTime();
```
``ScreenSpec`` interface creation:
```java
public interface ScreenSpec {
   public String getResolution();
   public int getRefreshRate();
   public int getResponseTime();
}
```
## Step 9
We then created a ``Screen`` class thatimplemets the ``ScreenSpec`` interface.\
This means that all the 3 methods in the interface will be implemented in the ``Screen`` class\
Code snippet:
```java
public class Screen implements ScreenSpec {
   String resolution;
   int refreshRate;
   int responseTime;

   public Screen(String resolution,int refereshRate,int responseTime){
	this.resolution=resolution;
	this.responseTime=responseTime;
	this.refreshRate=refereshRate;
   }

   @Override
   public String getResolution() {
	
	return this.resolution;
   }

   @Override
   public int getRefreshRate() {
	return refreshRate;
   }

   @Override
   public int getResponseTime() {
	
	return responseTime;
   }

   public String toString() {
       return "Resolution: "+ this.resolution+"RefreshRate: "+this.refreshRate+"ResponseTime:"+"-->"+this.responseTime;
   }	
}
```
A ``toString()`` method is created to display the screen details. The method is of ``String`` type\
Code Snippet:
```java
public String toString() {
    return "Resolution: "+ this.resolution+"RefreshRate: "+this.refreshRate+"ResponseTime:"+"-->"+this.responseTime;
}	
```
The class has a constrator that is used during instantiation of an object\
Code Snippet:
```java
public Screen(String resolution,int refereshRate,int responseTime){
     this.resolution=resolution;
     this.responseTime=responseTime;
     this.refreshRate=refereshRate;
}
```
The attributes will be assigned values when creating a class instance\
## Step 10
created a driver class ``Driver_Sreen`` for Screen to test the functionality\

Code snippet:
```java
public class Driver_Screen {
   public static void main(String[] args) {                //main method 
	Screen screen =new Screen("111x540", 20, 30);      // instance of the class 
	System.out.println(screen.toString());	           //get the details of the screen 
   }	
}
```
## Step 11 
Class ``MoviePlayer`` created which extends ``Product`` and implements ``MultimediaControl`` \
```java
public class MoviePlayer extends Product implements MultimediaControl
```
The class has 2 attributes ``screen`` and ``monitorType`` which are assigned appropriate types to them 
For our case thay are assigned as shown in the below code snippet:\
```java
Screen screen;
MovieType monitorType;
```
The class uses a field ``name`` from its parent class.This is displayed in the class constractor\
```java
public MoviePlayer(String name,Screen screen,MovieType monitorType) {
    super(name);
    this.screen = screen;
    this.monitorType=monitorType;		
}
```
The class implements all the methods from the interface ``MultimediaControl``\
code snippet:\
```java
@Override
public void play() {
    System.out.println("Play--Video");
		
}

@Override
public void stop() {
    System.out.println("Stop--Video");	
}

@Override
public void previous() {
    System.out.println("<<<<<Previous");		
}

@Override
public void next() {
    System.out.println("next>>>>>>>");
		
}
```
The Details of the Movieplayer can be displayed in the console by the ``toString()`` method 
```java
public String toString() {
    return super.toString()+"\n"+"MonitorType: "+monitorType+"\n"+"ScreenDetails: --->"+this.screen.toString();
}
```
## Step 12
Created a Driver class ``Driver_MoviePlayer`` to test the functionality of the ``MoviePlayer`` class \
```java

public class Driver_MoviePlayer {
    public static void main(String[] args) { 
    	//first class instance 
	Screen screen=new Screen("102x1", 30, 40);
	MoviePlayer mvp=new MoviePlayer("Silicon Valley", screen, MovieType.LCD);
	System.out.println(mvp.toString());
	

	//second class instance 
	Screen screen2=new Screen("102x1", 30, 40);
	MoviePlayer mvp2=new MoviePlayer("Motley Crew ", screen2, MovieType.LED);
	System.out.println(mvp2.toString());
	
   }
	
}
```
Before creating the instance a ``Screen`` class instance was created to be passed in ``MoviePlayer`` constractor \
eg:
```java
Screen screen=new Screen("102x1", 30, 40);
```
The monitorType was fetched from the Enum ``MovieType``, which can be ``MovieType.LCD`` or ``MovieType.LED
Display the movie Details using the print statement below \
```java
System.out.println(mvp2.toString());
```
## Step 13
```java
public class Driver_movie_audio {
	public static void main(String[] args) {
		/**
		 * @step--13
		 * demonstartes that any class that implements 
		 * the multicontrol interface would be able to 
		 * be instantiated and use its methods used no matter 
		 * if its an audio or movie player 
		 */
	
		Audioplayer aud_p=new Audioplayer("a", "cgctctc");
		aud_p.play();
		aud_p.previous();
		aud_p.next();
		aud_p.stop();
		
		Screen scrn=new Screen("120x100", 0, 0);
		MoviePlayer mov_p=new MoviePlayer("b",scrn, MovieType.LCD);
		mov_p.play();
		mov_p.stop();
		mov_p.previous();
		mov_p.next();

	}
}

```
demonstartes that any class that implements the multicontrol 
interface would be able to be instantiated and use its methods used no matter  if its an audio or movie player 
## Step 14 
We created the a class ``Compare`` that implemets the Interface ``Comparator``
```java
public class Compare implements Comparator<Product> 
```
Inside the class we have a method compare that handles all the comparisons.Its an overriden method from the 
Interface ``Comparator``
```java
@Override
public int compare(Product arg0, Product arg1) {
   return  arg0.getName().compareTo(arg0.getName());
}
```
we imported ``java.util.Comparator``
The whole class implementstion is as shown below.
```java


public class Compare implements Comparator<Product> {
  @Override
  public int compare(Product arg0, Product arg1) {
      return  arg0.getName().compareTo(arg0.getName());
  }
}
```

## Step 15 & 16
Using class ``Compare`` we can sort the products then use a ``for_loop`` to list them.
We created a object ``com`` as shown 
```java
Comparator<Product> com=new Compare();
```
Sort the items as shown below
```java
Collections.sort(Product.products,com);
```
for loop that iterates in a Big O(N) time compelexity and lists the products.
```java
for(Product l :Product.products){
  System.out.println(l);
  System.out.println("-------------------------------");	
}
```
The whole print functions is as shown below.It was created inside the driver class.
```java
public static void  print(){
  Comparator<Product> com = new Compare();
  Collections.sort(Product.products,com);
  //sorted 
  for(Product l :Product.products){
    System.out.println(l);
    System.out.println("-------------------------------");	
  }
}
```
                                                ``END``

