class Node:
    def __init__(self, value=None):
        self.value = value
        self.next = None

    def __str__(self):
        return str(self.value)

class LinkedList:
    def __init__(self):
        self.head = None
        self.tail = None

    def __iter__(self):
        curNode = self.head
        while curNode:
            yield curNode
            curNode = curNode.next

class Queue:
    def __init__(self):
        self.linkedList = LinkedList()

    def __str__(self):
        values = [str(x) for x in self.linkedList]
        return ' '.join(values)

    def enqueue(self, value):
        newNode = Node(value)
        if self.linkedList.head == None:
            self.linkedList.head = newNode
            self.linkedList.tail = newNode
        else:
            self.linkedList.tail.next = newNode
            self.linkedList.tail = newNode

    def isEmpty(self):
      if self.linkedList.head == None:
          return True
      else:
          return False

    def dequeue(self):
        if self.isEmpty():
            return "The queue is empty"
        else:
            tempNode = self.linkedList.head
            if self.linkedList == self.linkedList.tail:
                self.linkedList.head = None
                self.linkedList.tail = None
            else:
                self.linkedList.head = self.linkedList.head.next
            return tempNode

    def peek(self):
        if self.isEmpty():
            return "The queue is empty"
        else:
            return self.linkedList.head

    def delete(self):
        self.linkedList.head = None 
        self.linkedList.tail = None 

custQueue = Queue()
for x in range(1,6):
    custQueue.enqueue(x)

print(custQueue)
print(custQueue.dequeue())
print(custQueue)
print(custQueue.peek())
custQueue.delete()

if custQueue.isEmpty():
    print('The queue is empty')
else:
    print(custQueue)
