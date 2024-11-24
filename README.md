# Red-Black Trees

## Introduction

A Red-Black Tree is a type of self-balancing Binary Search Tree (BST) that maintains balance through specific properties. It ensures that operations like insertion, deletion, and lookup can be performed in \( O(\log n) \) time. This efficiency makes Red-Black Trees suitable for applications such as database indexing, memory allocation, and associative containers (e.g., `std::map` in C++).

---

## Properties of Red-Black Trees

1. **Node Color**: Each node is colored either **red** or **black**.
2. **Root Property**: The root node is always **black**.
3. **Red-Black Property**: No two consecutive red nodes are allowed (a red node cannot have a red child).
4. **Black-Height Property**: All paths from any node to its null descendants must have the same number of black nodes.
5. **Binary Search Tree Property**: An in-order traversal of the tree results in sorted keys.

These properties help ensure the tree maintains near-perfect balance, with a height of at most \( 2\log(n+1) \).

---

## Core Operations

### 1. Insertion

- Insert the node as you would in a standard BST.
- Color the newly inserted node **red**.
- If any Red-Black Tree properties are violated, resolve these using **recoloring** and **rotations**.

#### Insertion Cases

- **Case 1**: New node is the root → Recolor it to black.
- **Case 2**: Parent is black → No violation occurs.
- **Case 3**: Both parent and uncle are red → Recolor parent and uncle black, and grandparent red.
- **Case 4**: Parent is red, uncle is black → Perform necessary rotations and recolor.

---

### 2. Deletion

- Remove the node as you would in a standard BST.
- If the removed node was **black**, resolve any violations by:
  - **Recoloring**: Adjust the colors of the nodes to maintain the Red-Black Tree properties.
  - **Double-Black Resolution**: Handle the extra blackness that can occur on a node after deletion.
  - **Rotations**: Perform left or right rotations to rebalance the tree and restore Red-Black properties.

#### Deletion Cases

- **Case 1**: Sibling is red → Perform a rotation and recolor.
- **Case 2**: Sibling and both its children are black → Recolor the sibling.
- **Case 3**: Sibling has at least one red child → Execute rotations and recolor.

---

### Rotations

Rotations are used to maintain the balance of the Red-Black Tree. They adjust the tree structure while preserving the BST property.

#### Left Rotation

A left rotation moves a node's right child to its position and shifts the subtree.

Before Rotation:

```
    x
     \
      y
     / \
    A   B
```

After Left Rotation:

```
    y
   / \
  x   B
 /
A
```

#### Right Rotation

A right rotation moves a node's left child to its position and shifts the subtree.

Before Rotation:

```
    y
   /
  x
 / \
A   B
```

After Right Rotation:

```
    x
   / \
  A   y
     /
    B
```

- Rotations ensure that the tree remains balanced and the Red-Black properties are restored without violating the Binary Search Tree (BST) property.
