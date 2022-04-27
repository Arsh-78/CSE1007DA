<h1 align="center" > Merkel Tree </h1>

  
* <h2>Introduction</h2>

Merkle tree is a fundamental part of blockchain technology. It is a mathematical data structure composed of hashes of different blocks of data, and which serves as a summary of all the transactions in a block. It also allows for efficient and secure verification of content in a large body of data. It also helps to verify the consistency and content of the data. Both Bitcoin and Ethereum use Merkle Trees structure. Merkle Tree is also known as Hash Tree.

The concept of Merkle Tree is named after Ralph Merkle, who patented the idea in 1979. Fundamentally, it is a data structure tree in which every leaf node labelled with the hash of a data block, and the non-leaf node labelled with the cryptographic hash of the labels of its child nodes. The leaf nodes are the lowest node in the tree.

* <h2> Architecture </h2>
![2](https://user-images.githubusercontent.com/76211430/165564402-dc25595e-8a86-4639-b7da-7f11b8574c4c.png)





A Merkle tree stores all the transactions in a block by producing a digital fingerprint of the entire set of transactions. It allows the user to verify whether a transaction can be included in a block or not.

Merkle trees are created by repeatedly calculating hashing pairs of nodes until there is only one hash left. This hash is called the Merkle Root, or the Root Hash. The Merkle Trees are constructed in a bottom-up approach.

Every leaf node is a hash of transactional data, and the non-leaf node is a hash of its previous hashes. Merkle trees are in a binary tree, so it requires an even number of leaf nodes. If there is an odd number of transactions, the last hash will be duplicated once to create an even number of leaf nodes.

The above example is the most common and simple form of a Merkle tree, i.e., Binary Merkle Tree. There are four transactions in a block: TX1, TX2, TX3, and TX4. Here you can see, there is a top hash which is the hash of the entire tree, known as the Root Hash, or the Merkle Root. Each of these is repeatedly hashed, and stored in each leaf node, resulting in Hash 0, 1, 2, and 3. Consecutive pairs of leaf nodes are then summarized in a parent node by hashing Hash0 and Hash1, resulting in Hash01, and separately hashing Hash2 and Hash3, resulting in Hash23. The two hashes (Hash01 and Hash23) are then hashed again to produce the Root Hash or the Merkle Root.

Merkle Root is stored in the block header. The block header is the part of the bitcoin block which gets hash in the process of mining. It contains the hash of the last block, a Nonce, and the Root Hash of all the transactions in the current block in a Merkle Tree. So having the Merkle root in block header makes the transaction tamper-proof. As this Root Hash includes the hashes of all the transactions within the block, these transactions may result in saving the disk space.



* <h2> Algorithm </h2>
A Merkle tree is constructed by recursively hashing pairs of nodes until there is only one hash.
a hash function acts as a “digital fingerprint” of some piece of data by mapping it to a simple string with a low probability that any other piece of data will map to the same string.

Each node is created by hashing the concatenation of its “parents” in the tree.

This function is used to check whether the given key is present in the Merkle tree or not. If it is present then it will return that node else it will return null.

Step 1: We will take tree and key as parameters.

Step 2: If the tree is null then we will return null.

Step 3: If the tree->key is equal to the key we will return the tree.

Step 4: If the key is smaller than tree->key then we will return find(tree->left, key)

Step 5: else return find(tree->right, key)

Add Operation in Merkle Tree
This function is used to add a node into the Merkle tree.

Algorithm to add a node in Merkle tree.

Step 1: We will take key and value as parameters.

Step 2: Take the hash(key) and store it in a variable called index.

Step 3: store (struct node*) arr[index].head in a pointer called tree of datatype node.

Step 4: create a new node with its key as key and value as value and both links as null.

Step 5: If the tree is null then assign the new node to the head and increment the size by 1.

Step 6: If the tree is not null then we will check if the key is already present in the tree using the find function.

Step 7: If the key is already present in the tree then we will update the value.

Step 8: If it is not present in the tree then we will use the insert function to insert the element.

Algorithm of insert function.

Step 1: It will take tree and item pointers of node data type as parameters.

Step 2: If item->key is smaller than tree->key and tree->left is null then assign the item to tree->left.

Step 3: If item->key is smaller than tree->key and tree->left is not null then call insert function with tree->left and item as parameters.

Step 4: If item->key is greater than tree->key and tree->right is null then assign the item to tree->right.

Step 5: If item->key is greater than tree->key and tree->right is not null then call insert function with tree->right and item as parameters.

Delete Operation in Merkle Tree
This function is used to delete a node from Merkle tree. If the key given is present in the Merkle tree then it will delete the node from the tree.

Algorithm to delete a node in Merkle tree.

Step 1: We will take a key as a parameter.

Step 2: Take the hash(key) and store it in a variable called index.

Step 3: store (struct node*) arr[index].head in a pointer called tree of datatype node.

Step 4: If the tree is null then the key is not present.

Step 5: If the tree is not null then we will check if the key is already present in the tree using the find function.

Step 6: If the find function returns null then the key is not present in the tree.

Step 7: If it is not null then we will use the remove function to delete the element.

Algorithm of remove function.

Step 1: It will take tree and key as parameters.

Step 2: If the tree is null then return null.

Step 3: If the key is smaller than the tree->key then tree->left is equal to remove(tree->left, key) and return tree.

Step 4: If the key is greater than the tree->key then tree->right is equal to remove(tree->right, key) and return tree.

Step 5: else if the tree->left is equal to null and the tree->right is equal to null then decrement the size and return tree->left.

Step 6: else if the tree->left is not equal to null and the tree->right is equal to null then decrement the size and return tree->left.

Step 7: else if tree->left is equal to null and tree->right is not equal to null then decrement the size and return tree->right.

Step 8: else assign tree->left to a pointer called left of data type node.

Step 9: While left->right is not equal to null, left is equal to left->right.

Step 10: tree->key is equal to left->key.

Step 11: tree->value is equal to left->value.

Step 12: tree->left is equal to remove(tree->left, tree->key).

Step 13: Return tree.


* <h2> References </h2>
* Google
* Github
* https://www.javatpoint.com/blockchain-merkle-tree
* https://www.linkedin.com/pulse/merkle-tree-its-implementation-java-nikhil-goyal/
* https://iq.opengenus.org/merkle-tree/
