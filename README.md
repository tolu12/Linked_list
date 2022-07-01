# Linked_list
how to [[create and display alinked list], [how to insert at the begining , ending and any position of the linked list], [how to delete at the begining, ending and at any position of the linked list]]
class Linked_list:
    """ 
    Singly linked list 
    """

    def __init__(self):
        self.head = None

    def is_empty(self):
        return self.head is None

    def size(self):
        """ 
         Returns the number of nodes in a list 
         takes O(n) time 
        """
        current = self.head
        count = 0

        while current:
            count += 1
            current = current.next_node

        return count

    def in_add(self, data):
        """ 
         Adds a new node containing data at the head of the linked list 
        """
        new_node = Node(data)
        new_node.next_node = self.head
        self.head = new_node

    def in_end(self, data):
        """ 
        Adds a new node at the end of a linked list 
 
        """
        new_node = Node(data)
        temp = self.head
        while temp.next_node:
            temp = temp.next_node

        temp.next_node = new_node

    def in_pos(self, pos, data):
        """ 
        Add a new node at any position 
        """
        new_node = Node(data)
        temp = self.head
        for i in range(pos - 1):
            temp = temp.next_node
        new_node.data = data
        new_node.next_node = temp.next_node
        temp.next_node = new_node

    def del_begin(self):
        """ 
        Deletes a Node at the beginning 
        """
        temp = self.head
        self.head = temp.next_node
        temp.next_node = None

    def del_end(self):
        """ 
        Deletes a Node at the end 
        """
        temp = self.head.next_node
        prev = self.head
        while temp.next_node is not None:
            temp = temp.next_node
            prev = prev.next_node
        prev.next_node = None

    def del_pos(self, pos):
        """ 
        Deletes a node at any given position 
        """
        temp = self.head.next_node
        prev = self.head
        for i in range(1, pos - 1):
            temp = temp.next_node
            prev = prev.next_node
        prev.next_node = temp.next_node

    def search(self, key):
        """ 
         search for the first node containing data that matches the key 
         Returns the Node or None if not found 
 
         Takes O(n) time 
        """
        current = self.head

        while current:
            if current.data == key:
                return current
            else:
                current = current.next_node
        return None

    def __repr__(self):
        """ 
        Returns a string representation of the list 
        Takes O(n) time 
        """

        nodes = []
        current = self.head

        while current:
            if current is self.head:
                nodes.append("[Head: %s]" % current.data)
            elif current.next_node is None:
                nodes.append("[Tail: %s]" % current.data)
            else:
                nodes.append("[%s]" % current.data)

            current = current.next_node
        return '-> '.join(nodes)


l = Linked_list()
l.in_add(1)
l.in_add(2)
l.in_add(3)
l.in_add(4)
l.in_add(5)
n= l.search(7)

print(l)
print(n)
