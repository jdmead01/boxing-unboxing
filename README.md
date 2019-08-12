# Boxing/Unboxing

In C#, every variable needs an associated type at compile time due to its use of static typing. This is pretty useful for keeping things consistent and avoiding some datatype errors. But what are we to do when we need to make a collection with different types of data? We could make a jagged array, but then we would have to know the sizes of our data sets as well. We know that lists are able to handle varying lengths of data, but we are back to now being able to store only one type of data. Well, luckily, with a little implementation trick that exists in C# called Boxing, we can construct a list of one data type that holds data of different data types. Wait, that seems quite contradictory, doesn't it? The way this works is that almost all types can be cast to the generic **object** type. So, if you construct a list of type **object** you will be able to hold varying types in one collection. The process of boxing is very powerful, but we have to keep in mind that when working with any data in a collection of this type we have to **be sure to cast it back to its original type when retrieving it.** If we don't cast, or "unbox", the items in our List when we retrieve them, our code will only be able to treat them as if they were type **object**.


# Safely Unboxing

Note that though boxing/unboxing is a powerful tool, it can also be dangerous. If you were to unbox something to work with and attempt to cast it to a data type that it cannot conform to, the program will break at runtime even though the compiler may allow the operation at build-time. We need to be careful with unboxing values and handle any cases like this that may not go as planned. The simplest way is to make sure the value works for the type you are trying to cast it to before doing so. This can be done by leveraging the **is** keyword in a conditional statement.

```javascript
 //Box some string data into a variable
object BoxedData = "This is clearly a string";
//Make sure it is the type you need before proceeding
if (BoxedData is int) {
//This shouldn't run
    Console.WriteLine("I guess we have an integer value in this box?");
}
if (BoxedData is string) {
    Console.WriteLine("It is totally a string in the box!");
}
```
The  `is`  keyword allows us to discern what the real type of an object is when we unbox it, but to actually treat it as that type we will need to cast it. We can use explicit casting once we have determined the appropriate type. Unlike type conversion casting, unboxing casting doesn't create a new memory space, but changes how the system references the object. When unboxing, we also have the ability to use another form of casting called safe explicit casting.

## Safe Explicit Casting

Safe explicit casting uses the `as` keyword. Unlike explicit casting, if a safe cast fails it will simply return a null value rather than throwing an exception. The catch is that safe casts can only be used to cast to a nullable type. Some simple datatypes, such as int, are non-nullable, meaning that they can't store a null value; these datatypes cannot be used with safe casting.
```javascript
object ActuallyString = "a string";
string ExplicitString = ActuallyString as string;
 
// THIS WON'T WORK!!
object ActuallyInt = 256;
int ExplicitInt = ActuallyInt as int;
```
## Complete the Following Goals for the Assignment 

 - [ ] Create an empty List of type Object	
 - [ ] Add the following values to the list: 7, 28, -1, true, "chair"
 - [ ] Loop through the list and print all values (Hint: type inference might help here!)
 - [ ] Add all values that are int type together and output the sum
