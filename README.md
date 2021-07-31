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



