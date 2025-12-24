- A linked list is a linear data structure, in which the elements are not stored at contiguous memory locations. The elements in a linked list are linked using pointers as shown in the below image:
![[Pasted image 20240731203350.png]]
- A linked list is represented by a pointer to the first node of the linked list. **The first node is called the head**. If the linked list is empty, then the value of the head is NULL. Each node in a list consists of at least two parts:
	- Data
	- Pointer (Or Reference) to the next node
```python
# Node class
class Node:
	# Function to initialize the node object
    def __init__(self,data):
        self.data = data # Assign data
        self.next = None # Initialize
				        # next as null
        

# Linked List Class
class LinkedList:
	# Function to initialized the Linked List Object
    def __init__(self) -> None:
        self.head = None
```
 