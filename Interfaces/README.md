# Java Interfaces

## Some key points on Java Interfaces

- A class would not be able to implement multiple interfaces if the implementing interfaces have a variable with same name. 

- A class would not be able to implement multiple interfaces if the implementing interfaces contains methods having same name, same signature but different return type

- If a class implements multiple interfaces where in implemented interfaces have methods with same name then class will complie only when
	- Methods having same name have same signature and same return type as well or
	- Methods having same name have different signature regardless on return type

- Consider another scenario, two interfaces have same name, same signature but different return type. Parent class implements one of the interface and Child class extends Parent and implements the other interface. This will result in compilation error "incompatible with return type of parent class" unless the return type of overriding method in Child Class is covariant of return type in Parent class's overrriden method.

### Q1) Consider the below scenario

public interface InterfaceA {

	public static final int variableOfInterface=10;
	
	public static final float anotherVariableOfInterface=50;
	
	public void performOperation();
}

public interface InterfaceB {

	public static final int variableOfInterface=20;
	
	public static final int anotherVariableOfInterface=50;
	
	public void performOperation();
}

public class InterfaceImplementation implements InterfaceA,InterfaceB{

	public void performOperation() {
	
		System.out.println(variableOfInterface);
		
		System.out.println(anotherVariableOfInterface);
	}
}

### What is the output ?

### Answer: This will result in compilation error variables are ambigious for both the sysout.



### Q2) Consider the below scenario

public interface InterfaceA {

	public void getInputs(int a, int b);
	
	public void performOperation();
	
	public int getResult();
}

public interface InterfaceB {

	public void getInputs(float a, float b);
	
	public void performOperation();
	
	public float getResult();
}

public class InterfaceImplementation implements InterfaceA,InterfaceB{

	private int a,b=0;
	private float x,y=0.0f;
	
	public void performOperation() {
		float floatResult=getResult();
		int intResult=getResult();
		System.out.println(floatResult);
		System.out.println(intResult);
	}

	public float getResult() {
		return x*y;
	}        
	
	public int getResult() {
		return a*b;
	}   

	public void getInputs(int a, int b) {
		this.a=a;
		this.b=b;
	}
	
	public void getInputs(float a, float b) {
		this.x=a;
		this.y=b;
	}
}

### What is the output?

### Answer: Will result in compilation error on method getResult(). 
getResult() on line 69: Incompatible with InterfaceA.getResult()

getResult() on line 73: Duplicate method getResult()
