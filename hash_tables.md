# Hash Tables

##Linear Probing:
>###Logic
	1. Hash to key
	2. If address is open, insert elt
	3. Else, go to next address.
	4. Repeat from step 2 until inserted

>>###Pros: 	Quick and Dirty. Good Caching
>>###Cons: 	Clustering

##Quadratic Probing
>###Logic
  	1. Hash to key h(key)
  	2. Let j = 1
  	3. If address is open, insert elt.
  	4. Else, increment j and compute h(key) + j2 % M (where M is size of table)
  	5. Repeat from Step 3 until insertion
  
  >>###Pros: more efficient algorithm in a closed hash table, since it better avoids the clustering problem that can occur with linear probing, although it is not immune. It also provides good memory caching because it preserves some locality of reference
  >>###Cons: linear probing has greater locality and, thus, better cache performance.
  
##Double Hashing
>###Logic
  	1. Hash to key h<sub>1</sub>(key)
  	2. j = 1, select a q for some prime number q < M
  	3. If empty, insert elt
  	4. Else, compute h<sub>1</sub>(key) + j * h’(key)) mod M, where 
	   h’(key) = q – (h1(key) mod q)
	5. Repeat from Step 2 until insertion
  
>>###Pros: Since h1 and h’ are randomly, uniformly, and independently created hash functions, multiple collisions for close keys are rare, while maintaining good caching
>>###Cons: Heavier computation than other traditional collision resolution methods
  
##Separate Chaining
>###Logic
	1. Hash to key
	2. If address is open, insert elt
 	3. Else, append to the end of the singly linked list attached to h(key)
  
  >>###Pros: require only basic data structures with simple algorithms, and can use simple hash functions that are unsuitable for other methods
  >>###Cons: Singly Linked List Traversal
  >>###Side Note: Why Singly Linked List? Because memory overhead on any other data structure is theoretically unnecessary. There’s no reason why you can’t hash into a AVL tree, but that’s considered in cases of real world applications, and contributes little to theoretical understanding of separate chaining.
	
##Dynamic Hashing
>###Logic
	1. Load Factor = N / M or Number of Elts / Size of Table
	2. When Load Factor α (N/M) gets over a certain size (typically between ½ and ¾), it’s usually a good idea to resize the table.
	3. Resizing Table usually means M = M * 2
  
>>###Pros: Amortized Cost is relatively low. Good when you don’t know how many inputs you will need to add ahead of time.
>>###Cons: It’s a heavy payload when you do have to resize, which is inefficient in real life.
