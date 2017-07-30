## Method Overriding and Method Overloading

### Q1) What is covariant method overriding in Java? 

### Answer: 
Covariant method overriding is feature introduced in 1.5 version where return type of the overriding method is allowed to be a subtype of the overridden method's return type. It prevents
client side typecasting. 

public class MyFoo implements Cloneable
{
   public MyFoo clone()
   {
       // Implementation
   }
} 

Here client need not type cast MyFoo.clone()

### Q1) Can we override a method with different return types ? 

### Answer:

This will result in compilation error "incompatible with return type of parent class" unless the return type of overriding method in Child Class is covariant of return type in Parent class's overrriden method.