# 二叉树 Binary tree

## 结构描述

```
Class Node {

			V value;

			Node left;

			Node right;

			}
```

## 先序、中序、后序遍历

1. 先序遍历（==Preorder Traversal==）：从树的根节点出发，首先访问根节点，然后依次递归遍历左子树和右子树。在先序遍历中，根节点的访问发生在左右子树之前。

   **头左右**

   

2. 中序遍历（==Inorder Traversal==）：从树的根节点出发，首先递归遍历左子树，然后访问根节点，最后递归遍历右子树。在中序遍历中，根节点的访问发生在左子树之后，右子树之前。

3. 后序遍历（==Postorder Traversal==）：从树的根节点出发，首先递归遍历左子树，然后递归遍历右子树，最后访问根节点。在后序遍历中，根节点的访问发生在左右子树之后。

所谓先中后，指的都是root先、中、后。

子树：从一个根节点出发，下面的所有子数都算上。比如c-e-b是子树，但是c-d不是子树。

<img src="/Users/yyyang/Library/Application Support/typora-user-images/image-20231107125937307.png" alt="image-20231107125937307" style="zoom:50%;" />

<img src="/Users/yyyang/Library/Application Support/typora-user-images/image-20231107130421891.png" alt="image-20231107130421891" style="zoom:50%;" />

  //先序

**Java代码**

```
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    public TreeNode(int val) {
        this.val = val;
    }

}

public class BinaryTreeTraversal {
    public void preorderTraversal(TreeNode root) {
        if (root == null) {
            return;
        }
        System.out.print(root.val + " ");
        preorderTraversal(root.left);
        preorderTraversal(root.right);
    }

    public void inorderTraversal(TreeNode root) {
        if (root == null) {
            return;
        }
        inorderTraversal(root.left);
        System.out.print(root.val + " ");
        inorderTraversal(root.right);
    }
    
    public void postorderTraversal(TreeNode root) {
        if (root == null) {
            return;
        }
        postorderTraversal(root.left);
        postorderTraversal(root.right);
        System.out.print(root.val + " ");
    }

}
```

python代码

```
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

def preorderTraversal(root):
    if root is None:
        return
    print(root.val, end=" ")
    preorderTraversal(root.left)
    preorderTraversal(root.right)

def inorderTraversal(root):
    if root is None:
        return
    inorderTraversal(root.left)
    print(root.val, end=" ")
    inorderTraversal(root.right)

def postorderTraversal(root):
    if root is None:
        return
    postorderTraversal(root.left)
    postorderTraversal(root.right)
    print(root.val, end=" ")

# 创建一个二叉树示例

root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)
root.right.left = TreeNode(6)
root.right.right = TreeNode(7)

# 先序遍历

print("Preorder Traversal:")
preorderTraversal(root)
print()

# 中序遍历

print("Inorder Traversal:")
inorderTraversal(root)
print()

# 后序遍历

print("Postorder Traversal:")
postorderTraversal(root)
print()
```

可以发现，其实他们的区别就是打印的位置不一样！

![image-20231107131439941](/Users/yyyang/Library/Application Support/typora-user-images/image-20231107131439941.png)

继续以上面的二叉树为例：

一开始1⃣️，函数要求向左数执行，所以来到了2⃣️，（一定要记住只有发现null的时候才会返回！！！！而2⃣️的2⃣️.left不为空，所以我们继续2⃣️.left而不是继续向右），

然后继续到4⃣️，4⃣️继续看它的左，然后发现为空，于是向右执行，发现还是空，于是返回4⃣️，这次是第三次到4⃣️了，也就是最后一次到4⃣️了，于是return回了2⃣️。。。。





所以是这样的：1⃣️2⃣️4⃣️4⃣️4⃣️2⃣️5⃣️5⃣️5⃣️2⃣️1⃣️3⃣️6⃣️6⃣️6⃣️3⃣️7⃣️7⃣️7⃣️3⃣️1⃣️

先序：第一次到达某个节点的时候，打印



