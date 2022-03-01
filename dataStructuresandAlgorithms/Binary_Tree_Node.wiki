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
[[Traversals]]

class TreeNode:
    def __init__(self,data):
        self.data = data
        self.leftChild = None
        self.rightChild = None

def preOrderTraversal(rootNode):
    if not rootNode:
        return
    print(rootNode.data)
    preOrderTraversal(rootNode.leftChild)
    preOrderTraversal(rootNode.rightChild)

def inOrderTraversal(rootNode):
    if not rootNode:
        return
    inOrderTraversal(rootNode.leftChild)
    print(rootNode.data)
    inOrderTraversal(rootNode.rightChild)

def postOrderTraversal(rootNode):
    if not rootNode:
        return
    postOrderTraversal(rootNode.leftChild)
    postOrderTraversal(rootNode.rightChild)
    print(rootNode.data)

# --- Test Tree

rootNode = TreeNode('N1')
N2 = TreeNode('N2')
N3 = TreeNode('N3')
N4 = TreeNode('N4')
N5 = TreeNode('N5')
N6 = TreeNode('N6')
N7 = TreeNode('N7')
N8 = TreeNode('N8')
N9 = TreeNode('N9')

N4.leftChild = N8
N4.rightChild = N9

N2.leftChild = N4
N2.rightChild = N5

N3.leftChild = N6
N3.rightChild = N7

rootNode.leftChild = N2
rootNode.rightChild = N3

# ------ Examples

print('Example of Preorder Traversal')
preOrderTraversal(rootNode)
# LOGIC: Root Node  -->  Left Subtree --> Right Subtree
# * N1 -> N2 -> N4 -> N8 -> N9 -> N5 -> N3 -> N6 -> N7
print('---------------------------\n')

print('Example of Inorder Traversal')
inOrderTraversal(rootNode)
# * N8 -> N4 -> N9 -> N2 -> N5 -> N1 -> N6 -> N3 -> N7
print('---------------------------\n')


print('Example of Postorder Traversal')
postOrderTraversal(rootNode)
# * N8 -> N9 -> N4 -> N5 -> N2 -> N6 -> N7 -> N3 -> N1
print('---------------------------\n')
