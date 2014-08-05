ArrayQueue
==========
public class ArraqyQueue {
	private int QSIZE;
	private int[] queue;
	private int nItems;

	public ArrayQueue(int size) {
		this.QSIZE = size;
		this.queue = new int[this.QSIZE];
	}

	public void showQueue() {
		int i;
		for(i = 0; i < this.QSIZE; i++) {
			System.out.println("Queue[" + i + "] = " + this.queue[i] + "\n");
		}
	}

	public boolean isFull() {
		if (this.nItems == this.QSIZE) {
			System.out.println("QUEUE is FULL");
			return true;
		} else {
			return false;
		}
	}

	public boolean isEmpty() {
		if (this.nItems == 0) {
			System.out.println("QUEUE is Empty");
			return true;
		} else {
			return false;
		}
	}

	public boolean enqueue(int num) {
		System.out.println("Trying to enqueue " + num + "... ");
		if (!this.isFull()) {
			this.queue[nItems] = num;
			System.out.println("Added " + num);
			this.nItems++;
			return true;
		} else {
			System.out.println("Failed to enqueue " + num);
			return false;
		}
	}

	public int dequeue() {
		System.out.println("Dequeueing... ");
		if (!this.isEmpty()) {
			int num = this.queue[0];
			System.out.println("Removed " + num);
			this.rearrangeQueue();
		} else {
			System.out.println("Failed to dequeue. ");
		}
		return 0;
	}

	private void rearrangeQueue() {
		System.out.println("Rearrangeing Queue");
		int[] temp = new int[this.nItems];
		int i;
		for (i = 0; i < (this.nItems - 1); i++) {
			temp[i] = this.queue[i + 1];
		}
		this.nItems--;
		for(i = 0; i < this.QSIZE; i++) {
			if (i <= this.nItems) {
				this.queue[i] = temp[i];
			} else {
				this.queue[i] = 0;
			}
		}
	}

	public int peekFront() {
		return this.queue[0];
	}		

	public int peekRear() {
		return this.queue[this.QSIZE-1];
	}	

}
=================================================================================================================
public class ArrayQueueApp {
	
	public static void main(String[] args) {

		ArrayQueue queue = new ArrayQueue(8);

		System.out.println("------------------");
		queue.enqueue(15);
		queue.enqueue(1);
		queue.enqueue(19);
		queue.enqueue(31);
		queue.enqueue(12);
		queue.enqueue(30);
		queue.enqueue(5);
		queue.enqueue(16);

		System.out.println();
		System.out.println("-------------------");
		queue.showQueue();

		System.out.println();
		System.out.println("-------------------");
		System.out.println(queue.dequeue());
		System.out.println(queue.dequeue());
		System.out.println(queue.dequeue());

		System.out.println();
		System.out.println("-------------------");
		queue.showQueue();

		System.out.println();
		queue.peekFront();
		queue.peekRear();

	}

}
