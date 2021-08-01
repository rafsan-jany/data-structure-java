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

**QUEUE**
1. FIFO
2. set front = - 1, rear = -1 when queue is empty and size as capacity
3. for first element enQueue, set front = 0 for first element enQueue and rear = rear + 1
4. for every enQueue, increment the rear as rear = rear + 1, 
5. for every deQueue, increment the front as front = front + 1,
6. for last element deQueue, set front = -1 and rear = -1,
7. check isFull when front == 0 and rear == size -1,
8. check isEmpty when front == -1;

```

public class Queue {
	
	int[] arr;
	int front;
	int rear;
	int capacity;
	
	public Queue(int size) {
		capacity = size;
		front = -1;
		rear = -1;
		arr = new int[size];
	}
	
	public void enQueue(int x) {
		if(isFull()) {
			System.out.println("Queue is full");
		}else {
			if(front == -1) 
				front = 0;
			rear++;
			arr[rear] = x;
			System.out.println("Inserted " + x);
		}
	}
	
	public int deQueue() {
		int y;
		if(isEmpty()) {
			System.out.println("Queue is empty");
			return (-1);
		}else {
			y = arr[front];
			if(front >= rear) {
				front = -1;
				rear = -1;
			}else {
				front++;
			}
			System.out.println("Delete : " + y);
			return y;
		}	
	}

	public boolean isEmpty() {
		if(front == -1)
			return true;
		return false;
	}

	public boolean isFull() {
		if(front == 0 && rear == capacity -1 )
			return true;
		return false;
	}
	
	public void display() {
		if(isEmpty()) {
			System.out.println("Empty queue");
		}else {
			for(int i = front; i <= rear; i++)
				System.out.println(arr[i]);
			System.out.println("rear index : " + rear);
		}
	}
	
	public static void main(String[] args) {
		
		Queue queue = new Queue(4);
		
		// not possible for empty queue
		queue.deQueue();
		
		queue.enQueue(1);
		queue.enQueue(2);
		queue.enQueue(3);
		queue.enQueue(4);
		
		// not possible as queue is full
		queue.enQueue(5);
		
		System.out.println("display after enqueue.");
		queue.display();
		
		queue.deQueue();
		
		System.out.println("display after deQueue.");
		queue.display();
	}
}

```

**CIRCULAR QUEUE**

```

public class CircularQueue {
	
	int[] arr;
	int front, rear;
	int capacity;
	
	public CircularQueue(int size) {
		arr = new int[size];
		front = -1;
		rear = -1;
		capacity = size;
	}
	
	public void enQueue(int x) {
		if(isFull()) {
			System.out.println("Queue is full");
		}else {
			if(front == -1) 
				front = 0;
			// for circular
			rear = (rear + 1) % capacity;
			arr[rear] = x;
			System.out.println("inseted : " + x);
		}
	}
	
	public int deQueue() {
		int y;
		if(isEmpty()) {
			System.out.println("Queue is empty");
			return -1;
		}else {
			y = arr[front];
			if(front == rear) {
				front = -1;
				rear = -1;
			}else {
				// for circular
				front = (front + 1) % capacity;
			}
			System.out.println("deleted : " + y);
			return y;
		}
	}
	
	public boolean isFull() {
		// if front postiong is 0 and the queue is full so rear is the last element position : size - 1
		if(front == 0 && rear == capacity -1)
			return true;
		// if rear starts from the beginning again and front is one step ahead from the rear
		if(front == rear + 1) 
			return true;
		return false;
	}

	public boolean isEmpty() {
		if(front == -1)
			return true;
		return false;
	}
	
	public void display() {
		int i = 0;
		if(isEmpty())
			System.out.println("Queue is empty");
		else
			for(i = front; i != rear; i = (i + 1) % capacity)
				System.out.println("item : " + arr[i]);
			System.out.println("item : " + arr[i]);
			System.out.println("rear -> " + rear);
	}
	
	public static void main(String[] args) {
		
		CircularQueue circular = new CircularQueue(5);
		
		// no element in queue
		circular.deQueue();
		
		//enqueue 
		circular.enQueue(1);
		circular.enQueue(2);
		circular.enQueue(3);
		circular.enQueue(4);
		circular.enQueue(5);
		
		//display
		circular.display();
		
		//dequeue
		circular.deQueue();
		
		circular.display();
		//enqueue
		circular.enQueue(6);
		
		//display
		circular.display();
	}
}

```

**LINKED LIST**

```
public class LinkedList {
	//head of the list
	Node head;
	
	//linked list node
	static class Node{
		int value;
		Node next;
		
		Node(int d){
			value = d;
			next = null;
		}
	}
	
	//insert at the beginning 
	public void insertAtBeginning(int newData) {
		// initialize new node
		Node newNode = new Node(newData);
		//new node points to the head 
		newNode.next = head;
		// head becomes the newNode as now newNode is the first node
		head = newNode;
	}
	
	//insert after a node
	public void insertAfter(Node prevNode, int newData) {
		if(prevNode == null) {
			System.out.println("The given previous node cannot be null");
			return;
		}
		//initialize new node
		Node newNode = new Node(newData);
		//newNode points the next of the given prevNode
		newNode.next = prevNode.next;
		//prevNode points the newNode as it is entered right after the prevNode
		prevNode.next = newNode;
	}
	
	//insert at the end
	public void insertAtEnd(int newData) {
		Node newNode = new Node(newData);
		
		// if list is empty
		if(head == null) {
			// new node is the first node as head
			head = new Node(newData);
			return;
		}
		
		//newNode is the last node so newNode.next is null 
		newNode.next = null;
		
		Node last = head;
		while(last.next != null) 
			last = last.next;
		
		last.next = newNode;
		return;
	}
	
	//delete a node
	void deleteNode(int position) {
		//head == null means linked list is empty
		if(head == null)
			return;
		//store head node
		Node temp = head;
		
		//head removed
		if(position == 0) {
			//set new head
			head = temp.next;
			return;
		}
		
		//17->21->32->41->55 list
		//0- 1- 2- 3- 4 position
		//if we want to delete position 4, means 55, we need to select position 3 which value is 32
		// we need to run loop for 2 because temp.next point 21 when i = 0
		//find the previous node of the node to be deleted
		for(int i = 0; temp != null && i < position -1; i++)
			temp = temp.next;
		
		//if position is more than number of nodes
		if(temp == null || temp.next == null)
			return;
		
		// temp.next is the node to be deleted
		//temp.next.next is the node which is the next node of the deleted node
		Node next = temp.next.next;
		
		//set the temp.next to the next node of the deleted node
		// means unlink the deleted node from the list
		temp.next = next;
	}
	
	//print the linked list
	public void printList() {
		Node tnode = head;
		while(tnode != null) {
			System.out.println(tnode.value);
			tnode = tnode.next;
		}
	}
	
	public static void main(String[] args) {
		
		LinkedList llist = new LinkedList();
		
	    llist.insertAtEnd(1);
	    llist.insertAtBeginning(2);
	    llist.insertAtBeginning(3);
	    llist.insertAtEnd(4);
	    llist.insertAfter(llist.head.next, 5);

	    System.out.println("Linked list: ");
	    llist.printList();

	    System.out.println("\nAfter deleting an element: ");
	    llist.deleteNode(3);
	    llist.printList();	
	}
}

```

