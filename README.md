<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Queue Based Question</title>
    <script>

  //Reverse a queue using recursion.


/*function reverseQueue(queue){
    if(queue.length===0)
        return;

        const front =queue.shift();

        reverseQueue(queue);

        queue.push(front);
    }
const queue=[1,2,3,4,5];
console.log("original Queue",[...queue]);
reverseQueue(queue);
console.log("reversed Queue",queue);


   class Queue {
    constructor(){
        this.items=[];
    }
    enqueue(element){
        this.items.push(element);
    }
    dequeue(){
        if(this.isEmpty())
            return null;
            return this.items.shift();
        }
        isEmpty(){
            return this.items.length===0;
        }
        size(){
            return this.items.length;
        }
        front(){
            if(this.isEmpty)
                return null;
                return this.items[0];
            }
            print(){
                console.log(this.items);
            }
            reverse(){
                if(this.isEmpty())
                return;

                const frontElement= this.dequeue();
                this.reverse();
                this.enqueue(frontElement);
            }
        }

        const myQueue = new Queue();
        [1,2,3,4,5].forEach(num=>myQueue.enqueue(num));
        console.log("original queue");
        myQueue.print();
        myQueue.reverse();
        myQueue.print();
        console.log("size",myQueue.size());   


//  Check if a given sequence of operations is valid for a queue.


function Queue(operations){
    const queue=[];


    for(const op of operations){
        if(op.op==='enqueue'){
            queue.push(op.value);
        }
        else if (op.op== 'dequeue'){
            if(queue.length===0 || queue[0] !==op.value) {
                return false;
            }
            queue.shift();
        }
        else {
            return false;
        }
    }
    return true;
}
const ops1 = [
  { op: 'enqueue', value: 1 },
  { op: 'enqueue', value: 2 },
  { op: 'dequeue', value: 1 },
  { op: 'enqueue', value: 3 },
  { op: 'dequeue', value: 2 },
  { op: 'dequeue', value: 3 }
];

const ops2 = [
  { op: 'enqueue', value: 1 },
  { op: 'dequeue', value: 2 }
];

console.log("Ops1 valid:", Queue(ops1)); 
console.log("Ops2 valid:", Queue(ops2)); 

   

// Implement a Deque (Double-ended queue


// Node class for doubly linked list
class Node {
  constructor(value) {
    this.value = value;
    this.prev = null;
    this.next = null;
  }
}

class Deque {
  constructor() {
    this.front = null;
    this.rear = null;
    this.size = 0;
  }


  isEmpty() {
    return this.size === 0;
  }

 
  insertFront(value) {
    const newNode = new Node(value);
    if (this.isEmpty()) {
      this.front = this.rear = newNode;
    } else {
      newNode.next = this.front;
      this.front.prev = newNode;
      this.front = newNode;
    }
    this.size++;
  }


  insertRear(value) {
    const newNode = new Node(value);
    if (this.isEmpty()) {
      this.front = this.rear = newNode;
    } else {
      newNode.prev = this.rear;
      this.rear.next = newNode;
      this.rear = newNode;
    }
    this.size++;
  }
  deleteFront() {
    if (this.isEmpty()) {
      throw new Error("Deque is empty");
    }
    const value = this.front.value;
    this.front = this.front.next;
    if (this.front === null) {
      this.rear = null;
    } else {
      this.front.prev = null;
    }
    this.size--;
    return value;
  }


  deleteRear() {
    if (this.isEmpty()) {
      throw new Error("Deque is empty");
    }
    const value = this.rear.value;
    this.rear = this.rear.prev;
    if (this.rear === null) {
      this.front = null;
    } else {
      this.rear.next = null;
    }
    this.size--;
    return value;
  }

  
  getFront() {
    if (this.isEmpty()) {
      throw new Error("Deque is empty");
    }
    return this.front.value;
  }

 
  getRear() {
    if (this.isEmpty()) {
      throw new Error("Deque is empty");
    }
    return this.rear.value;
  }

 
  getSize() {
    return this.size;
  }

 
  printDeque() {
    let result = [];
    let current = this.front;
    while (current) {
      result.push(current.value);
      current = current.next;
    }
    console.log("Deque:", result.join(" <-> "));
  }
}
const dq = new Deque();

dq.insertFront(10);
dq.insertRear(20);
dq.insertFront(5);
dq.insertRear(25);

dq.printDeque(); 

console.log("Front:", dq.getFront()); 
console.log("Rear:", dq.getRear());  

dq.deleteFront(); 
dq.deleteRear();  

dq.printDeque(); 

  


//Implement a priority queue using a heap  in javascripot and understand me what are saying this code tell me what is heap 

class MinHeap {
  constructor() {
    this.heap = [];
  }


  getParentIndex(i) { return Math.floor((i - 1) / 2); }
  getLeftChildIndex(i) { return 2 * i + 1; }
  getRightChildIndex(i) { return 2 * i + 2; }

  swap(i, j) {
    [this.heap[i], this.heap[j]] = [this.heap[j], this.heap[i]];
  }

  insert(value) {
    this.heap.push(value);
    this.heapifyUp();
  }


  heapifyUp() {
    let index = this.heap.length - 1;
    while (index > 0 && this.heap[this.getParentIndex(index)] > this.heap[index]) {
      this.swap(index, this.getParentIndex(index));
      index = this.getParentIndex(index);
    }
  }


  extractMin() {
    if (this.heap.length === 0) return null;
    if (this.heap.length === 1) return this.heap.pop();

    const min = this.heap[0];
    this.heap[0] = this.heap.pop();
    this.heapifyDown();
    return min;
  }


  heapifyDown() {
    let index = 0;
    const length = this.heap.length;

    while (this.getLeftChildIndex(index) < length) {
      let smallerChildIndex = this.getLeftChildIndex(index);

      if (
        this.getRightChildIndex(index) < length &&
        this.heap[this.getRightChildIndex(index)] < this.heap[smallerChildIndex]
      ) {
        smallerChildIndex = this.getRightChildIndex(index);
      }

      if (this.heap[index] < this.heap[smallerChildIndex]) break;

      this.swap(index, smallerChildIndex);
      index = smallerChildIndex;
    }
  }

  peek() {
    return this.heap[0];
  }

  isEmpty() {
    return this.heap.length === 0;
  }
}


const pq = new MinHeap();
pq.insert(10);
pq.insert(4);
pq.insert(15);
pq.insert(1);

console.log(pq.extractMin()); 
console.log(pq.extractMin()); 
console.log(pq.extractMin()); 






*/

    </script>
</head>
<body>
    
</body>
</html>
