# Java KnowledgeSharing

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

### What is the output ?

### Answer: Will result in compilation error on method getResult(). 
getResult() on line 69: Incompatible with InterfaceA.getResult()
getResult() on line 73: Duplicate method getResult()
