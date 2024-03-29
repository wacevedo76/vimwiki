--------------------------------------------------------------------------------
= Data Structures and Algorithms =
--------------------------------------------------------------------------------
  == Notes from books ==
--------------------------------------------------------------------------------
  [[A Common-Sense Guide to Data Structures and Algorithms]]
  [[Grokking Algorithms]]
--------------------------------------------------------------------------------
  == Notes ==

  === Some common Big O run times ===
  O(long n)                  | Also known as log time, Example: Binary Search
                             |
  O(n)                       | Also known as linear time, Example: Simple Search
                             |
  O(n * log n)               | Example: A fast sorting algorithm, like quicksort
                             |
  O(n**2)                    | Example: A slown sorting algorithm, like
                             |          selection sort
                             |
  O(n!)                      | Example: A really slow algorithm, like the
                             |          traveling saiesperson
--------------------------------------------------------------------------------
  == Recursion ==
  === When to use recursion ===
  - When we can easily breakdown a problem into similar subproblems
  - When we are fine with extra overhead (both in tim and space) that comes with it
  - When a quick working solution is preferable to an efficient one.
  - When traversing a tree
  - When memoization is used in recursion

  === How to write a recursive method in three steps ===
  :TODO
--------------------------------------------------------------------------------
  == Queue ==
  === Standard Queue operations ===
  [[dataStructuresandAlgorithms/Queue|Queue]] implemented as a Python array
  [[dataStructuresandAlgorithms/Queue2|Queue2]] implemented as a linked list in Python
  - Create Queue
  - Enqueue
  - Dequeue
  - Peek
  - isEmpty
  - isFull
  - deleteQueue
                             |
--------------------------------------------------------------------------------
  == Trees ==
  === Tree Terminology ===
  Here is an example of a [[dataStructuresandAlgorithms/Tree|Tree]] node in python
  Root                       | Top node without parent
  Edge                       | A link between parent and child
  Leaf                       | A node which does not have children
  Sibling                    | Children of the same parent
  Ancestor                   | parent, grandparent, greatgrandparent... of a node
  Depth of node              | a length of the path from root to node
  Heigh of node              | a length of the path from the node to the deepest node
  Depth of tree              | depth of root node
  Height of tree             | Height of root node
--------------------------------------------------------------------------------
  === Types of trees ===
  Here is an example of a [[dataStructuresandAlgorithms/Binary_Tree|Binary Tree]] as a python list

  * Full Binary Tree         | A tree whose nodes have 0 or two children.
  * Perfect Binary Tree      | A tree where all non Leaf nodes have two.
                             | Children and are at the samed depth.
  * Complete Binary Tree     | A tree where all levels are complete (nodes have.
                             | two children) except the last level, the last
                             | level has all keys as leftwise as possible.
  * Balanced Binary Tree     | All Leaf nodes are the at the same distance from
                             | the Root node (not any father than any other).
--------------------------------------------------------------------------------
  === Operations which can be performed on a Binary Tree ===
  * Creation of Tree
  * Insertion of a node
  * Deletion of a node
  * Travers all nodes
  * Deletion of tree
  Here is an example of A [[dataStructuresandAlgorithms/Binary_Tree_Node|Binary Tree Node]] in Python utilizing linked list pattern
--------------------------------------------------------------------------------
  === Traversal of Binary Tree ===
  Depth first search
  -  Preorder traversal
  -  In order traversal
  -  Post order traversal
  Breadth first seach
  - Level order traversal
  Here is a list and description of [[dataStructuresandAlgorithms/Traversals|Traversals]]
                             |
