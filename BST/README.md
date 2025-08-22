
# **Binary Search Tree Implementation in C++**

## **Description**

This repository contains a C++ implementation of a **Binary Search Tree (BST)**. A BST is a node-based binary tree data structure which has the following properties:
*   The left subtree of a node contains only nodes with keys lesser than the node's key.
*   The right subtree of a node contains only nodes with keys greater than the node's key.
*   The left and right subtree each must also be a binary search tree.
*   There must be no duplicate nodes.

This implementation provides the fundamental operations for a BST, including **insertion**, **deletion**, **searching**, and **traversal**.

## **Code Structure**

The implementation consists of two main parts: a **`Node`** structure and a **`BST`** class.

### **`Node` Struct**
The **`Node`** struct represents a single node within the Binary Search Tree. It contains:
*   **`key`**: An integer value that the node holds.
*   **`left`**: A pointer to the left child node.
*   **`right`**: A pointer to the right child node.
*   **`parent`**: A pointer to the parent node.

### **`BST` Class**
The **`BST`** class encapsulates the Binary Search Tree and its operations.

#### **Public Methods**
*   **`BST()`**: Constructor to initialize an empty BST.
*   **`inorderTreeWalk()`**: Prints the keys of the BST in sorted order.
*   **`treeSearch(int key)`**: Searches for a node with a given key and returns a pointer to it if found, otherwise `nullptr`.
*   **`treeInsert(int key)`**: Inserts a new node with the given key into the BST.
*   **`treeDelete(Node* z)`**: Deletes a given node `z` from the BST.
*   **`treeSuccessor(Node* x)`**: Finds the successor of a given node `x` in the BST.
*   **`getRoot()`**: Returns a pointer to the root of the BST.

#### **Private Methods**
*   **`inorderTreeWalk(Node* x)`**: The recursive helper function for inorder traversal.
*   **`treeMinimum(Node* x)`**: Finds the node with the minimum key in a subtree rooted at `x`.
*   **`transplant(Node* u, Node* v)`**: A utility function used by `treeDelete` to replace one subtree as a child of its parent with another subtree.

## **Features**

*   **Insertion**: Add new elements to the tree while maintaining the BST property.
*   **Deletion**: Remove elements from the tree. The implementation correctly handles three cases:
    1.  The node to be deleted is a leaf (has no children).
    2.  The node has only one child.
    3.  The node has two children.
*   **Search**: Efficiently find an element in the tree.
*   **Inorder Traversal**: Traverse the tree and print the elements in ascending order.
*   **Successor Finding**: Find the next largest element in the tree for any given node.
*   **Minimum Finding**: Find the element with the smallest key in a given subtree.

## **How to Use**

To use this BST implementation, you can include the code in your C++ project. Here is a simple example of how to create a `BST` object and use its methods:

```cpp
#include <iostream>
// Include the BST code here

int main() {
    BST myBST;

    // Insert some values
    myBST.treeInsert(15);
    myBST.treeInsert(6);
    myBST.treeInsert(18);
    myBST.treeInsert(3);
    myBST.treeInsert(7);
    myBST.treeInsert(17);
    myBST.treeInsert(20);
    myBST.treeInsert(2);
    myBST.treeInsert(4);
    myBST.treeInsert(13);
    myBST.treeInsert(9);

    // Print the inorder traversal of the BST
    std::cout << "Inorder traversal: ";
    myBST.inorderTreeWalk(); // Output: 2 3 4 6 7 9 13 15 17 18 20

    // Search for a node
    Node* searchResult = myBST.treeSearch(7);
    if (searchResult != nullptr) {
        std::cout << "Node with key 7 found." << std::endl;
    } else {
        std::cout << "Node with key 7 not found." << std::endl;
    }

    // Find the successor of a node
    Node* node_13 = myBST.treeSearch(13);
    if (node_13 != nullptr) {
        Node* successor = myBST.treeSuccessor(node_13);
        if (successor != nullptr) {
            std::cout << "Successor of 13 is: " << successor->key << std::endl; // Output: 15
        }
    }

    // Delete a node
    Node* nodeToDelete = myBST.treeSearch(6);
    if (nodeToDelete != nullptr) {
        myBST.treeDelete(nodeToDelete);
        std::cout << "Inorder traversal after deleting 6: ";
        myBST.inorderTreeWalk(); // Output: 2 3 4 7 9 13 15 17 18 20
    }

    return 0;
}
