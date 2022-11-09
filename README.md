# Concurrent Hash Table Lookup And Acceleration

Ying Jiang(yingj2), Yinyue Wu(yinyuew)

Webpage: https://yinyuewu.github.io/pp_proj/

## Summary

We are going to implement a concurrent open-address hash table with different settings. Specifically, we first explore locking mechanisms on CPU OpenMP implementation: coarse-grained lock, fine-grained lock, read-write lock, and elaborate on lock-free mechanism. We will evaluate with alternatives of storing keys and values together, or with extra space for fast key lookup on the buckets. Finally, we are going to utilize SIMD and CUDA to accelerate the hash table operations. 

## Background

Hash Table, also known as Hash Map, is a widely used data structure in all places of software systems. It maps keys to values. A hash table uses a hash function to compute an index into an array, from which the value can be found. A hash table provides insert, lookup, and delete operations in constant time. 

A collision could happen in a HashMap, when two or more keys produce the same hash value and hence point to the same bucket location. There are two common methods to resolve the collision: linear probing and chaining. Linear probing searches the table for the closest following free location and inserts the new key there. Chaining resolves collisions by allowing each slot to hold a reference to a collection of items with the same key.

The standard implementations of hash tables in many programming languages are not thread-safe, but multi-thread access is the norm in many applications. Therefore, in this project we are going to implement a concurrent hash table so that multiple threads can operate on the same hash table simultaneously. 
