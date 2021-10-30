  `               +--+`
  `               |N1|`
  `               +--+`
  `              /     \`
  `             /       \`
  `          +--+        +--+`
  `          |N2|        |N3|`
  `          +--+        +--+`
  `         /    \      /    \`
  `        /      \    /      \`
  `       +--+  +--+  +--+  +--+`
  `       |N4|  |N5|  |N6|  |N7|`
  `       +--+  +--+  +--+  +--+`
  `      /    \`
  `     /      \`
  `    +--+  +--+`
  `    |N8|  |N9|`
  `    +--+  +--+`
[[Binary_Tree_Node|Binary Tree Node]]

Preorder Traversal of Binary Tree:
  LOGIC: Root Node  -->  Left Subtree --> Right Subtree
  * N1 -> N2 -> N4 -> N8 -> N9 -> N5 -> N3 -> N6 -> N7
  - Last node which is visited is lastmost righ Leaf on right Subtree.

InOrder Traversal of Binary Tree
  LOGIC: Left Subtree -> Root Node -> Righ Subtree
  * N8 -> N4 -> N9 -> N2 -> N5 -> N1 -> N6 -> N3 -> N7

PostOrder Traversal of Binary Tree
  LOGIC: Left Subtree -> Right Subtree -> Root Node
  * N8 -> N9 -> N4 -> N5 -> N2 -> N6 -> N7 -> N3 -> N1
