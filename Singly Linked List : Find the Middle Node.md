# 📚 Singly Linked List : Find the Middle Node of a Singly Linked List Using Recursion

This Python program demonstrates how to find the middle node of a singly linked list using recursion. The program calculates the middle element by utilizing two pointers, with one pointer moving one step at a time (slow) and the other moving two steps at a time (fast). When the fast pointer reaches the end of the list, the slow pointer will be at the middle node.

## 🎯 Aim

To write a Python program that:
- Creates a singly linked list.
- Uses recursion to find the middle node of the list.
- In case of an even number of nodes, it returns the second middle element.

## 🧠 Algorithm

1. **Node Class**: 
   - Define a `Node` class to represent each node in the singly linked list. Each node has two attributes: `data` and `next`.
   
2. **LinkedList Class**:
   - Define a `LinkedList` class that manages the linked list with methods to:
     - `append(data)`: Add a new node to the end of the list.
     - `get_middle_recursive(slow, fast)`: A recursive helper function to find the middle node using two pointers (slow and fast).
     - `find_middle()`: A method to call the recursive function and return the middle node's data.

3. **Input**:
   - First, the program reads an integer `n`, representing the number of elements in the linked list.
   - Then, it reads `n` space-separated integers to form the linked list.

4. **Recursive Middle Finding**:
   - The `get_middle_recursive` method uses two pointers to traverse the list:
     - The `slow` pointer moves one step at a time.
     - The `fast` pointer moves two steps at a time.
   - When the `fast` pointer reaches the end, the `slow` pointer will be at the middle node.

5. **Output**:
   - The program prints the middle element. If the list has an even number of nodes, it returns the second middle element.

---

## 💻 Program

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
        else:
            temp = self.head
            while temp.next:
                temp = temp.next
            temp.next = new_node

    def get_middle_recursive(self, slow, fast):
        # Base case: fast reaches end
        if fast is None or fast.next is None:
            return slow

        return self.get_middle_recursive(slow.next, fast.next.next)

    def find_middle(self):
        if self.head is None:
            return None
        middle_node = self.get_middle_recursive(self.head, self.head)
        return middle_node.data


ll = LinkedList()

n = int(input("Enter number of elements: "))

elements = list(map(int, input("Enter elements: ").split()))

for i in range(n):
    ll.append(elements[i])

middle = ll.find_middle()

if middle is not None:
    print("Middle element:", middle)
else:
    print("List is empty")

## Sample Input & Output
Input:

Enter number of elements: 5

Enter elements: 10 20 30 40 50

Output:

Middle element: 30

Even Case Example:

Enter number of elements: 6

Enter elements: 10 20 30 40 50 60

Middle element: 40

## Result
The program successfully:

Creates a Singly Linked List

Uses recursion with slow & fast pointers

Finds the middle node efficiently

Returns the second middle element for even-sized lists


