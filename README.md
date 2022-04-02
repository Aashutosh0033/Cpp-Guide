![cpp2](https://user-images.githubusercontent.com/83531337/160971771-8d8c2451-acfe-4313-8d61-bb802c1423a4.png)


<br>

 *This repo contains all the important concepts of cpp which makes it powerful and unique.*<br><br><br>
 
 
 # C++
Cpp is a general purpose programming language which was developed as an enchancement to C langauge to include the Object-Oriented paradigm.It is an imperative and Compiled language. It is a middle-level language which renders it the advantage of programming low-level (drivers, kernels,etc) and high-level (Games, GUI, desktop apps) applications.
<br><br><br>
 
 
 
 # Object Oriented Programming
 
 <br>
 
 **Concepts**
 
 

<details>
  <summary>Classes and Objects</summary>
    <br>- Objects memory allocation & using Arrays in Classes<br>
     - Static Data member and Methods<br>
     - Array of Objects and Passing Objects as function Arguments<br>
     - Friend Functions<br>
     - Friend Classes and Member Friend Functions<br>
</details>

    
<details>
  <summary>Constructors and Destructors</summary>
    <br>- Default Constructors<br>
    - Parameterized Constructors<br>
    - Copy Constructors<br>
    - Constructors Overloading<br>
    - Constructors with default arguments<br>
    - Dynamic Initialization of Objects using Constructors<br>
    - Initialization list in Constructors
    - Destructors<br>
</details>


<details>
 <summary>Inheritance</summary>
   <br>- Syntax and Visibility modes<br>
   - Single Inheritance<br>
   - Multilevel Inheritance<br>
   - Multiple Inheritance<br>
   - Heirarchical Inheritance<br>
   - Hybrid Inheritance<br>
   - Ambiguity Resolution in Inheritance<br>
   - Virtual Base Class <br>
   - Constructors in Derived in Class<br>
</details>



<details>
 <summary>Pointers</summary>
   <br>- new and delete keywords<br>
   - Pointers to objects and Arrow Operators<br>
   - Array of Objects <br>
   - this Pointer<br>
</details>


<details>
   <summary>Polymorphism</summary>
     <br>- Introduction <br>
     - Pointers to Derived Class<br>
     - Virtual Functions <br>
     - Abstract Base Class and Pure Virtual Functions<br>
</details>

<br><br>


## Classes and Objects

**Objects memory allocation and using Arrays in classes:**
The way memory is allocated to variables and functions is different in classes even thought they both are from same class. The memory is only allocated to the variables of the class when the object is created. The memeory is not allocated to variables when the class is declared. At the same time every variable will have different value for different object, so each object has a an individual copy of variables. But The memory is allocated to functions only when the class is created. So the objects don't have individual copies of the functions, only one copy is shared by all the objects.<br> 

<br>

Arrays are used to store multiple values of the same data type. An Array is useful when multiple variables are required, we can create a single array instead and store multiple values in it.<br>
For Ex. <br>
class Shop<br>
{<br>
    int itemId[100];<br>
    int itemPrice[100];<br>
    int counter;<br>

public:<br>
    void initCounter(void) { counter = 0; }<br>
    void setPrice(void);<br>
    void displayPrice(void);<br>
};<br><br>

void Shop ::setPrice(void)<br>
{<br>
    cout << "Enter Id of your item no " << counter + 1 << endl;<br>
    cin >> itemId[counter];<br>
    cout << "Enter Price of your item" << endl;<br>
    cin >> itemPrice[counter];<br>
    counter++;<br>
}<br><br>

**Static Data members and Methods:**
When static data memhers is created, there is only one copy of the variable shared different objects of the class. <br>
<br>
When static methods are created, they become independent of any object and class. Static methods can only access static members and static methods. <br>

<br>

**Array of Objects and Passing Objects as Arguments:**
An Array of objects is declared in the same way as the other data_type array is declared. An array of objects consists of class objects as its elements. If the array consists of class objects, it is called an Array of Objects. <br>
For Ex.<br>
class Employee<br>
{<br>
    int id;<br>
    int salary;<br>
<br>
public:<br>
    void setId(void)<br>
    {<br>
        salary = 122;<br>
        cout << "Enter the id of employee" << endl;<br>
        cin >> id;<br>
    }<br>
<br>
   void getId(void)<br>
    {<br>
        cout << "The id of this employee is " << id << endl;<br>
    }<br>
};<br>
<br>
<br>
int main()<br>
{<br>
    Employee fb[4];<br>
    for (int i = 0; i < 4; i++)<br>
    {<br>
        fb[i].setId();<br>
        fb[i].getId();<br>
    }<br>
<br>
   return 0;<br>
}<br>

<br><br>

Objects can be passed as function arguments. This is useful when we want to assign values of passed object to the current object. <br>
For Ex.<br>
class complex{<br>
    int a;<br>
    int b;<br>
<br>
   public: <br>
        void setData(int v1, int v2){<br>
            a = v1;<br>
            b = v2;<br>
        }<br>
<br>
   void setDataBySum(complex o1, complex o2){<br>
            a = o1.a + o2.a;<br>
            b = o1.b + o2.b;<br>
        }<br>
<br>
   void printNumber(){<br>
            cout<<"Your complex number is "<<a<<" + "<<b<<"i"<<endl;<br>
        }<br>
};<br>

<br><br>

int main(){<br>
    complex c1, c2, c3;<br>
    c1.setData(1, 2);<br>
    c1.printNumber();<br>
<br>
    c2.setData(3, 4);<br>
    c2.printNumber();<br>
<br>
    c3.setDataBySum(c1, c2);<br>
    c3.printNumber();<br>
    return 0;<br>
}<br>

<br><br>

**Friend Functions:**

Friend fuctions are the functions that have the access to the private data members of the class, even though they are not defined inside the class. It is necessary to write the prototype of the friend function. One necessary thing to note that, if we have written the prototype of the friend function in the class it will not make it the member of the class. <br>
For Ex.<br>
class Complex{<br>
    int a, b;<br>
    friend Complex sumComplex(Complex o1, Complex o2);<br>
    public:<br>
        void setNumber(int n1, int n2){<br>
            a = n1;<br>
            b = n2;<br>
        }<br>
<br>
        // Below line means that non member - sumComplex funtion is allowed to do anything with my private parts (members)<br>
        void printNumber(){<br>
            cout<<"Your number is "<<a<<" + "<<b<<"i"<<endl;<br>
        }<br>
};<br>

Complex sumComplex(Complex o1, Complex o2){<br>
    Complex o3;<br>
    o3.setNumber((o1.a + o2.a), (o1.b + o2.b))<br>
    ;<br>
    return o3;<br>
}<br>


<br>

int main(){<br>

   Complex c1, c2, sum;<br>
   c1.setNumber(1, 4);<br>
   c1.printNumber();<br>

   c2.setNumber(5, 8);<br>
   c2.printNumber();<br>
<br>
   sum = sumComplex(c1, c2);<br>
   sum.printNumber();<br>

   return 0;<br>
}<br>

Properties of Friend Friend Function : <br>
* Not in the scope of class
* Since it is not in the scope of class, it cannot be called from the object of the class.
* A friend function can be invoked without the help of any object.
* Usually contains objects as arguments.
* Can be declared under public and private access modifier it will not make any difference.
* It cannot acess members directly by their names, it has to use (object_name.member_name) .


<br><br>

**Friend Classes and Member Friend Functions:**
 
 Friend Classes are those classes that have permission to access the private members of the class in which they are declared. The main thing to note here is that if a class is made friend of another class, it can access all the private members of the class.<br>
 For Ex. <br>
 // Forward declaration<br>
class Complex;<br>
<br>
class Calculator<br>
{<br>
public:<br>
    int add(int a, int b)<br>
    {<br>
        return (a + b);<br>
    }<br>
<br>
    int sumRealComplex(Complex, Complex);<br>
    int sumCompComplex(Complex, Complex);<br>
};<br>

<br>

class Complex<br>
{<br>
    int a, b;<br>
    // Individually declaring functions as friends<br>
    // friend int Calculator ::sumRealComplex(Complex, Complex);<br>
    // friend int Calculator ::sumCompComplex(Complex, Complex);<br>
<br>
    // Aliter: Declaring the entire calculator class as friend<br>
    friend class Calculator;<br>
<br>
public:<br>
    void setNumber(int n1, int n2)<br>
    {<br>
        a = n1;<br>
        b = n2;<br>
    }<br>
<br>
    void printNumber()<br>
    {<br>
        cout << "Your number is " << a << " + " << b << "i" << endl;<br>
    }<br>
};<br>
<br>
int Calculator ::sumRealComplex(Complex o1, Complex o2)<br>
{<br>
    return (o1.a + o2.a);<br>
}<br>
<br>
int Calculator ::sumCompComplex(Complex o1, Complex o2)<br>
{<br>
    return (o1.b + o2.b);<br>
}<br>

<br><br>


## Constructors and Destructors







 
 
 # Pointers & References
  
   <br>
   
 <details>
    <summary>Pointers</summary>
    <br>- What are Pointers<br>
    - Null Pointers<br>
    - Pointer Arithmetics<br>
    - Pointers vs Arrays<br>
    - Pointer to Pointer<br>
    - Passing Pointer to functions <br>
    - Return Pointer from functions<br>
</details>
 <details>
    <summary>References</summary>
    <br>- What are References<br>
    - References as Parameters<br>
    - References as Return Value<br>
    - Pointers vs References<br>
</details>


## Pointers

**What are Pointers:**
Pointers are basically variables used to store the address or the memory location of other varibles.<br><br>


![How-Pointer-Works-In-C](https://user-images.githubusercontent.com/83531337/161263377-ea9d9220-8856-4352-820a-9cfe051efcba.png)

Syntax to declare pointers: <br>
   data_type* ptr_name; <br>
    <br>
   For Ex: int a = 10; <br>
           int* ptr = &a; <br>
   
  <br>
  
  In the above example variable a stores value 10 in it. And after that a pointer is created and assigned it to the address of variable a. <br> <br>
  
  * To access the address of a variable, we use the unary operator &(ampersand) that returns the address of the variable. 
  * One more operator is *(asterisk) which is used for two things - (i) To declare a pointer (ii) To access the value stored inside the pointer(That is also called Dereferencing). 

 <br> <br>
 
 
 **Null Pointers:**
 
 Poiters can be assigned Null value when declared. It is a good practice to assign null value to pointers in case you do not have exact address to assign. <br> For Ex: int* ptr = NULL ;
 
  <br> <br>
  
  **Pointer Arithmetics:**
  
  As Pointers are numeric values, it is obvious that we can perform Arithmetic Operations on it. There are few useful Arithmetic Operations which can be performed on pointers <br>
* Increment(++)
* Decrement(--)
* An integer can be added to a pointer
* An integer can be subtracted from a pointer

Pointer Arithmetic is meaningless unless performed on an Array<br>
Pointer contains addresses. Adding two addresses makes no sense, because we may not know what it is pointing to. But subtracting two contiguos addresses may give us an offset which can be added to any address to get the next address.<br>

<br>

**Pointers vs Arrays:**

There is a close relationship between pointers and arrays. Pointers and Arrays are interchangeable in many cases. For ex a pointer that points to start of an array can access the elements either by Array-style indexing or by pointer arithmetics.<br>
Note: An Array name is also the pointer to itself.<br>
For ex: int arr[3] = {1,2,3};<br>
        cout<<arr;<br>
        //output<br>
        address of first elements memory location 

<br><br>


**Array of Pointers:**

You can use an Array to store collection pointers to int,char or any data type.<br>

<br>

**Pointer to Pointer:**

You can assign pointer to pointer. That means creating a pointer to store the value of other pointer.<br>
The syntax for pointer to pointer is as follows: <br>
int a = 10;<br>
int* ptr1 = &a;<br>
int** ptr2 = &ptr1;<br>


<br>

**Passing Pointer to functions:**

Passing an argument by reference or by address both enable the passed arguments to be changed in the calling functions by the called functions.<br>
For Ex. Passing pointers to functions<br>
int main(){<br>
int a = 1;<br>
int b = 2;<br>
swap(&a,&b);<br>
This will change the value of the variables inside the calling functions

<br><br>
 
 
 
**Return Pointer from functions:**

A function can return pointers to local variable,static variable and dynamically allocated memory as well.<br>
To do so, you have to declare a function returning a pointer.<br>
For Ex. int* my_function(){}<br>

<br>


## References 

**What are References:**
A referene name is an alias, or another name for an already existing variable. Once a reference is initialised with a variable, either the reference name or the variable name can be used to refer the variable.<br>

Syntax for reference:<br>
int a = 10;<br>
int &b = a;<br>
cout<<a;<br>
cout<<b;<br>
//output: <br>
10<br>
10<br>

<br>

**References as Parameters:**
Reference variables can used as function parameters. It is a more safer way to call functions. This is also known as call by reference.<br>
For Ex.<br>
int a = 1;<br>
int b = 2;<br>
swap(a,b);<br>
<br>
int swap(int& c, int& d){}<br>

<br>

**Reference as Return Value:**

You can return reference from functions as any other data type. When a function returns a reference, it infact returns an implicit pointer to its return value.This way a function can be used on the left side of an assignment statement.<br>
Syntax: return_type& func_name(){};<br>

<br>

**Pointers vs References:**

References are often confused with pointers but three major differences between references and pointers are −<br>
* You cannot have NULL references. You must always be able to assume that a reference is connected to a legitimate piece of storage.<br>
* Once a reference is initialized to an object, it cannot be changed to refer to another object. Pointers can be pointed to another object at any time.<br>
* A reference must be initialized when it is created. Pointers can be initialized at any time.<br>

<br><br>




 # Templates
 
 <br><br>








  
  
   
   
   


   


   
 
 
 
 
 
 
