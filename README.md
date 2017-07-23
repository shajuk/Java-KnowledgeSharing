# Java KnowledgeSharing

## Q1) What is the output ?

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
	@Override
	public void performOperation() {
	
		System.out.println(variableOfInterface);
		
		System.out.println(anotherVariableOfInterface);
	}
}

## Answer: This will result in compilation error "variableOfInterface is ambigious" for both the sysout.

