# CH 3: Linked Lists

---

## Notes
<div style="padding: 1%;background-color: #f2fafc;margin-bottom: 1%"></div>

#### 3.1 What is a Linked List?

A data structure used for storing collections of data. Properties:

* Successive elements are connected by pointers
* The last element points to `NULL`
* Can grow or shrink in size during execution of a program
* Can be made just as long as required (_until systems memory exhausts_)
* Does not waste memory space (_but takes some extra memory for pointers_). It allocates memory as list grows.

#### 3.5 Comparison of Linked Lists with Arrays and Dynamic Arrays

Parameter | Linked List | Array | Dynamic Array
----------|-------------|-------|-------------- 
Indexing | O(n) | O(1) | O(1)
Insertion/deletion at beginning | O(1) | O(n), if array is not full (_for shifting the elements_) | O(n)
Deletion at ending | O(n) | O(1) | O(n)
Insertion in middle or <br/>Deletion in middle | O(n) | O(n), if array is not full (_for shifting the elements_) | O(n)
Wasted space | O(n) (_for pointers_) | 0 | O(n)

#### 3.6 Singly Linked Lists

This list consists of a number of nodes in which each node has a next pointer to the following element. The link of the last node in the list is `NULL`.

```python

# Node of a Singly Linked List
class Node:

    def __init__(self):
        self.data = None
        self.next = None
    
    def set_data(self, data):
        self.data = data
    
    def get_data(self):
        return self.data
    
    def set_next(self, next):
        self.next = next
    
    def get_next(self, next):
        return self.next
    
    def has_next(self):
        return self.next != None

```

**Traversing the Linked List**

```python

def list_length(self):
    current = self.head
    count = 0

    while current != None:
        count += 1
        current = current.get_next()
    return count

```

Time Complexity: O(n) and Space Complexity: O(1)

**Inserting a Node**

```python

def insert_at_beginning(self, data):
    new_node = Node()
    new_node.set_data(data)

    if self.length == 0:
        self.head = new_node
    else:
        new_node.set_next(self.head)
        self.head = new_node
    self.length += 1

def insert_at_end(self, data):
    new_node = Node()
    new_node.set_data(data)

    current = self.head

    while current.get_next() != None:
        current = current.get_next()
    
    current.set_next(new_node)
    self.length += 1

def insert_at_pos(self, pos, data):
    if pos > self.length or pos < 0:
        return None
    else:
        if pos == 0:
            self.insert_at_beginning(data)
        else:
            if pos == self.length:
                self.insert_at_end(data)
            else:
                new_node = Node()
                new_node.set_data(data)
                count = 1
                current = self.head

                while count < pos-1:
                    count += 1
                    current = current.get_next()
                new_node.set_next(current.get_next())
                current.set_next(new_node)
                self.length += 1

```

Time Complexity: O(n) and Space Complexity: O(1)

**Deleting a Node**

```python

def delete_from_beginning(self):
    if self.length == 0:
        print("The list is empty")
    else:
        self.head = self.head.get_next()
        self.length -= 1

def delete_last_node_from_singly_listed_list(self):
    if self.length == 0:
        print("The list is empty")
    else:
        currentnode = self.head
        previousnode = self.head

        while currentnode.get_next() != None:
            previousnode = currentnode
            currentnode = currentnode.get_next()
        
        previousnode.set_next(None)
        self.length -= 1

def delete_from_linked_list_with_node(self, node):
    if self.length == 0:
        raise ValueError("List is empty")
    else:
        current = self.head
        previous = None
        found = False

        while not found:
            if current = node:
                found = True
            elif current is None:
                raise ValueError("Node not in Linked List")
            else:
                previous = current
                current = current.get_next()
        
        if previous is None:
            self.head = current.get_next()
        else:
            previous.set_next(current.get_next())
        self.length -= 1

def delete_value(self, value):
    currentnode = self.head
    previousnode = self.head

    while currentnode.next != None or currentnode.value != value:
        if currentnode.value == value:
            previousnode.next = currentnode.next
            self.length -= 1
            return
        else:
            previousnode = currentnode
            currentnode = currentnode.next
    print("The value provided is not present")

def delete_at_position(self, pos):
    count = 0
    currentnode = self.head
    previousnode = self.head

    if pos > self.length or pos < 0:
        print("The position does not exist")
    else:
        while currentnode.next != None or count < pos:
            count += 1
            if count == pos:
                previousnode.next = currentnode.next
                self.length -= 1
                return
            else:
                previousnode = currentnode
                currentnode = currentnode.next

```

Time Complexity: O(n) and Space Complexity: O(1)
