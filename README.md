# Java KnowledgeSharing

## Q1) What is the output ?

public interface InterfaceA {
	public static final int variableOfInterface=10;
	
	public void performOperation();
}

public interface InterfaceB {
	public static final int variableOfInterface=20;
	
	public void performOperation();
}
public class InterfaceImplementation implements InterfaceA,InterfaceB{

	@Override
	public void performOperation() {
		System.out.println(variableOfInterface);
		
	}

