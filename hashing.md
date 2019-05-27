Hashing
=======

Resources:

https://en.wikipedia.org/wiki/Hash_table



* Remember that hashing does not mean having to use a sha-based function.
* As far as hashtable goes, the purpose of the hash function is to give you a value back, that you can use to figure out an index in the array where the key should be positioned.
* Collisions are OK but when possible, better avoided.
* There are multiple different strategies, one being using the modulo operator to determine the index

Consistent Hashing
================

Resources:

https://en.wikipedia.org/wiki/Consistent_hashing.

https://www.youtube.com/watch?v=zaRkONvyGr8

Consistent hashing ("ring") is a special kind of hashing such that, when a hash table is resized (let's say, in distributed environment, one of the hosts holding part of the table went down), only K/n keys need to be remapped on average, where K is the number of keys and n is the number of slots in the hash table.
  


