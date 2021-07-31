# data-structure-java
Data Structure implementation using java

**STACK**
1. LIFO
2. Set top == -1 and size as capacity
3. Push if stack is empty
4. Pop if stack has element
5. isEmpty if top == -1
6. isFull if top == capacity - 1 // top starts from 0 

``` 

public class Stack {
	
	private int[] arr;
	private int top;
	private int capacity;
	
	Stack(int size){
		arr = new int[size];
		top = -1;
		capacity = size;
	}
	
	
	public void push(int x) {
		if(isFull()) {
			System.out.println("Stack is full.");
			System.exit(1);
		}
		System.out.println("Inserting " + x);
    // top = top + 
    // arr[top] = x
    
		arr[++top] = x;
		
	}
	
	public int pop() {
		if(isEmpty()) {
			System.out.println("Stack is empty.");
			System.exit(1);
		}
    // arr[top];
    // top = top - 1;
    
		return arr[top--];
	}
	
	public int size() {
		return top + 1;
	}
	
	
	public Boolean isEmpty() {
		return top == -1;
	}
	
	public Boolean isFull() {
		return top == capacity - 1;
	}
	
	
	public void printStack() {
		for(int i = 0; i <= top; i++) {
			System.out.println(arr[i]);
		}
	}
	
	public static void main(String[] args) {
		Stack stack = new Stack(5);
		
		stack.push(1);
		stack.push(2);
		stack.push(3);
		stack.push(4);
		System.out.println("After push ");
		stack.printStack();
		
		stack.pop();
		System.out.println("After pop");
		stack.printStack();
	}
} 
```
