# 📝 Doubly Linked List: Search an Element

This Python program demonstrates the implementation of a **Doubly Linked List** where you can insert elements at both the beginning and the end of the list. Additionally, it allows you to search for a specific element in the list.

---

## 🎯 Aim

To write a Python program that:
- Implements a **Doubly Linked List** with functions to insert elements at the beginning and the end of the list.
- Implements a search function to check if a given element exists in the list.

---

## 🧠 Algorithm

1. **Step 1:** Define a class `Nodeq` with:
   - `data` to store the node's value.
   - `next` to store the reference to the next node.
   - `prev` to store the reference to the previous node.

2. **Step 2:** Define a class `DoublyLinkedList` with:
   - `head` to point to the first node.

3. **Step 3:** In the `DoublyLinkedList` class, define methods:
   - `insert_beginning(data)` to insert a node at the beginning.
   - `insert_end(data)` to insert a node at the end.
   - `search(data)` to search for an element in the list.

4. **Step 4:** Create an instance of `DoublyLinkedList`.
   - Insert elements at the beginning and end.
   - Search for specific elements.

---

## 💻 Program

class Nodeq:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None


class DoublyLinkedList:
    def __init__(self):
        self.head = None

    # Insert at beginning
    def insert_beginning(self, data):
        new_node = Nodeq(data)
        if self.head is None:
            self.head = new_node
        else:
            self.head.prev = new_node
            new_node.next = self.head
            self.head = new_node

    def insert_end(self, data):
        new_node = Nodeq(data)
        if self.head is None:
            self.head = new_node
        else:
            temp = self.head
            while temp.next:
                temp = temp.next
            temp.next = new_node
            new_node.prev = temp

    def search(self, key):
        temp = self.head
        position = 1
        while temp:
            if temp.data == key:
                return position
            temp = temp.next
            position += 1
        return -1

    def display(self):
        temp = self.head
        while temp:
            print(temp.data, end=" <-> ")
            temp = temp.next
        print("None")

dll = DoublyLinkedList()


dll.insert_beginning(30)
dll.insert_beginning(10)
dll.insert_end(50)
dll.insert_end(70)


print("Doubly Linked List:")
dll.display()

key = int(input("\nEnter element to search: "))
pos = dll.search(key)

if pos != -1:
    print(f"Element {key} found at position {pos}")
else:
    print(f"Element {key} not found in the list")

## Sample Output
Doubly Linked List:

10 <-> 30 <-> 50 <-> 70 <-> None

Enter element to search: 50

Element 50 found at position 3
## Result
The program successfully:

Implements a Doubly Linked List

Inserts elements at both beginning and end

Searches for a given element
Displays the position if found, otherwise shows not found

