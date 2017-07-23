# Java KnowledgeSharing

## Q1) Consider the below scenario

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

## Answer: This will result in compilation error variables are ambigious for both the sysout.

