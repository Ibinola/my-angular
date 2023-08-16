---
title: Hashmaps
description: blog description
published: true
---

# Hashmaps

Hash-tables
A hash-table is a list of paired values. The first item in the table is called a key and the second item a value
They store key-value pairs
- they have fast lookups, because once we have a key, we can find it's value. O(1)
- hashing is the process of converting a character to a number that signifies as the index to where value would be stored
- A = 1, B = 2, C = 3. the keys can
- under the hood, hashtables store data in a bunch of cells in a row similar to an array. Each cell has a corresponding number
- for every key-value pair, each value is stored at the index of the key, after the key has been hashed.
	- ACE hashes into 15, since ACE = 1 * 3 * 5 = 15, so "star" gets placed into cell 15
- hashmaps only add keys once, can only store unique values

**Hashtable lookups**

To find the value associated with "bad", the computer executes two simple steps: 
1. The computer hashes the key we’re looking up: BAD = 2 * 1 * 4 = 8. 
2. Since the result is 8, the computer looks inside cell 8 and returns the value stored there. In this case, that is the string, "evil"

Just as we hashed the key to insert the value in the appropriate cell, we can hash the key again to find where we previously put that value.
It now becomes clear why looking up a value in a hash table is typically O(1): it’s a process that takes a constant amount of time. The computer hashes the key, turns it into a number, and jumps to the index with that number to retrieve the value stored there.

We can only do O(1) lookups when using a key to find the value. If, on the other hand, we want to use a value to find its associated key, we cannot take advantage of the hash table’s fast lookup ability.
This is because the whole premise of the hash table is that the key determines the value’s location. But this premise only works in one direction: we use the key to find the value. The value does not determine the key’s location, so we have no way to easily find any key without combing through all of them.

**How are the keys stored**
While this detail may vary from language to language, some languages store the keys next to the values themselves. This is useful in the case of collisions. Each key can exist only once in the hash table, but there can be multiple instances of a value.
In many languages, if we try to store a key-value pair where the key already exists, it simply overwrites the old value while keeping the same key.

**Dealing w collisions**

Trying to add data to a cell that is already filled is known as a collision. One classic approach for handling collisions is known as separate chaining. When a collision occurs, instead of placing a single value in the cell, it places in it a reference to an array.

A hash table's efficiency goes up as the number of collisions goes down

**The great balancing act**

A good hash table strikes a **balance of avoiding collisions while not consuming lots of memory**
To accomplish this, computer scientists have developed the following rule of thumb: 
- For every 7 data elements stored in a hash table, it should have 10 cells.
