original from https://github.com/gibsjose/cpp-cheat-sheet

# C++ Data Structures and Algorithms Cheat Sheet
## 1. Data Structures
### 1.0 Overview of Containers

#### C++ and Python Syntax

| C++ | similar to Python |
|-|-|
| pair, tuple | tuple(), () |
| string | str() "", '' |
| array, vector, deque | list(), [] |
| unordered_map, unordered_set (hash map, hash table) | dict(), set(), {} |
| list, forward_list (singlely/doublely linked list) | |
| map, set (binary tree, BST) | |
| stack, queue, priority_queue (heap) | |

```python
t1 = tuple()  # Empty tuple
t2 = ()       # Empty tuple
t3 = (1, 2)   # Tuple with values
t4 = tuple([1, 2, 3])  # Tuple from list
```
```cpp
#include <tuple>
#include <utility>
std::pair<int, int> p1 = {1, 2};  // Pair initialization
std::tuple<int, double, char> t1 = {10, 3.14, 'A'};  // Tuple initialization
```
```python
s1 = str()    # Empty string
s2 = ""       # Empty string
s3 = ''       # Empty string
s4 = "hello"  # String with value
s5 = 'world'  # String with value
```
```cpp
#include <string>
std::string s1 = "";   // Empty string
std::string s2 = "hello";  // String with value
```
```python
a1 = list()  # Empty list (like a dynamic array/vector)
a2 = []      # Empty list
a3 = [1, 2, 3]  # List with values
```
```cpp
#include <array>
#include <vector>
#include <deque>
std::array<int, 3> arr = {1, 2, 3};  // Fixed-size array
std::vector<int> vec = {1, 2, 3};    // Vector (dynamic array)
std::deque<int> dq = {1, 2, 3};      // Deque
```
```python
m1 = dict()   # Empty dictionary (like an unordered_map)
m2 = {}       # Empty dictionary
m3 = {"key": "value", "a": 1}  # Dictionary with values
s1 = set()    # Empty set (like an unordered_set)
s2 = {1, 2, 3}  # Set with values
```
```cpp
#include <unordered_map>
#include <unordered_set>
std::unordered_map<std::string, int> umap = {{"apple", 1}, {"banana", 2}};  // Unordered map
std::unordered_set<int> uset = {1, 2, 3};  // Unordered set
```
```cpp
#include <map>
#include <set>
std::map<std::string, int> ord_map = {{"apple", 1}, {"banana", 2}};  // Ordered map (BST)
std::set<int> ord_set = {1, 2, 3};  // Ordered set (BST) // ascending order
std::set<int, std::greater<int>> desc_set = {3, 2, 1}; // Ordered set (BST) // descending order
// After initialization, the elements will be stored in sorted order, 
```
```cpp
#include <stack>
#include <queue>
std::stack<int> stk;  // Stack (LIFO)
std::queue<int> q;    // Queue (FIFO)
std::priority_queue<int> pq;  // Max-Heap by default
std::priority_queue<int, std::vector<int>, std::greater<int>> min_pq;  // Min-Heap
```

#### Properties
| | |
|-|-|
|Container Adaptors| Container adaptors are not full container classes, but classes that provide a specific interface relying on an object of one of the container classes (such as deque or list) to handle the elements. The underlying container is encapsulated in such a way that its elements are accessed by the members of the container adaptor independently of the underlying container class used.
|Sequence|Elements in sequence containers are ordered in a strict linear sequence. Individual elements are accessed by their position in this sequence.
|Contiguous storage |The elements are stored in contiguous memory locations, allowing **constant time random access to elements**. Pointers to an element can be offset to access other elements.
|Linked list|Each element keeps information on how to locate the next element, allowing constant time insert and erase operations after a specific element (even of entire ranges), but no direct random access.
|Doubly-linked list| Each element keeps information on how to locate the next and the previous elements, allowing constant time insert and erase operations before or after a specific element (even of entire ranges), but no direct random access.
|Fixed-size aggregate|The container uses implicit constructors and destructors to **allocate the required space statically**. Its size is compile-time constant. **No memory or time overhead**. 
|Dynamic array(deque) |Generally implemented as a dynamic array, it allows direct access to any element in the sequence and provides relatively fast **addition/removal** of elements at the **beginning or the end of** the sequence.
|Dynamic array(vector) |Allows **random access** to any element in the sequence, even through pointer arithmetics, and provides relatively fast **addition/removal** of elements **at the end of** the sequence.
|Associative|Elements in associative containers are referenced by their key and not by their absolute position in the container.
|Ordered|The elements in the container follow a strict order at all times. All inserted elements are given a position in this order.
|Unordered|Unordered containers organize their elements using hash tables that allow for fast access to elements by their key.
|Set|The value of an element is also the key used to identify it.
|Map|Each element associates a key to a mapped value: Keys are meant to identify the elements whose main content is the mapped value.
|Multiple equivalent keys|Multiple elements in the container can have equivalent keys.
|Unique keys|No two elements in the container can have equivalent keys.
|Allocator-aware|The container uses an allocator object to dynamically handle its storage needs.

- Key: type of element key
- T: type of element value
- Compare: A binary predicate that takes two element keys as arguments and returns a bool.
- Alloc: Type of the allocator object used to define the storage allocation model
- Hash: A unary function object type that takes an object of type key type as argument and returns a unique value of type size_t based on it. 
- Pred: A binary predicate that takes two arguments of the key type and returns a bool.
- Container: Type of the internal underlying container object where the elements are stored.
- N: Size of the array, in terms of number of elements.
- <img src="https://github.com/user-attachments/assets/2c9e62c3-aa89-4b30-89aa-1fb3ee5d2d81" width=600/>

#### Type: Sequence
| library | class | data structure | features |
|-|-|-|-|
| array | T, N | Basic Array | Sequence, Contiguous storage, Fixed-size aggregate, O(1) Random Access([index]) |
| vector| T, Alloc | Dynamic Array | Sequence, Contiguous storage, Dynamic Array(tail), Allocator-aware, O(1) Random Access([index]) |
| deque | T, Alloc | Double Ended Queue |Sequence, Non-Contiguous storage, Dynamic Array(head,tail), Allocator-aware, O(1) Random Access([index]) | 
|forward_list | T, Alloc | Singly Linked List |Sequence, Non-Contiguous storage, Linked List(next), Allocator-aware, O(N) Linear Access | 
|list | T, Alloc | Doubly Linked List | Sequence, Non-Contiguous storage, Linked List(next,prev), Allocator-aware, O(N) Linear Access |

#### Type: Adaptors
| library | class | data structure | features |
|-|-|-|-|
|stack| T, Container | LIFO Stack (`deque`, vector, list, forward_list) | empty, size, back, push_back, pop_back |
|queue|T, Container | FIFO Queue (`deque`, list) | empty, size, front, back, push_back, pop_front |
|priority_queue|T, Container, Compare | Priority Queue a.k.a. Max-Heap or Min-Heap (`vector`, deque) | empty, size, front, push_back, pop_back, Random Access(private) |

#### Type: Associative
| library | class | data structure | features |
|-|-|-|-|
|set| T, Compare, Alloc  | Binary Search Tree (nodes, vector, deque) | Associative, Ordered, Set(key=val), Unique-Keys. Allocator-aware, logN Access(iter) |  
|multiset| T, Compare, Alloc  | Binary Search Tree (nodes, vector, deque) | Associative, Ordered, Set(key=val), Multiple-equivalent-keys, Allocator-aware, logN Access(iter)| 
|map| Key, T, Compare, Alloc  | Binary Search Tree (nodes, vector, deque) | Associative, Ordered, Map(key&val), Unique-Keys, Allocator-aware, logN Access([key]) | 
|multimap| Key, T, Compare, Alloc | Binary Search Tree (nodes, vector, deque) | Associative, Ordered, Map(key&val), Multiple-equivalent-keys, Allocator-aware, logN Access([key]) | 

#### Type: Unordered Associative
| library | templete params | data structure | features |
|-|-|-|-|
|unordered_set| Key, Hash, Pred, Alloc | Hash Table | Associative, Unordered, Set(key=val), Unique-Keys. Allocator-aware, O(1) Random Access(iter) |  
|unordered_multiset| Key, Hash, Pred, Alloc | Hash Table | Associative, Unordered, Set(key=val), Multiple-equivalent-keys. Allocator-aware, O(1) Random Access(iter) |
|unordered_map | Key, T, Hash, Pred, Alloc | Hash Table | Associative, Unordered, Map(key&val), Unique-Keys. Allocator-aware, O(1) Random Access([index]) |  
|unordered_multimap | Key, T, Hash, Pred, Alloc | Hash Table | Associative, Unordered, Map(key&val), Multiple-equivalent-keys. Allocator-aware, O(1) Random Access([index]) |

#### Complexity
<img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/General/Data%20Structures.png" width=900/>

- n! > 2^n > n^2 > nlgn > n > lgn > 1
<img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/General/Complexity%20Chart.png" width=900/>

#### How to choose your data structure
<img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/General/Data%20Structures%20Selection.png" width=900/>

-------------------------------------------------------

### 1.1 Array `std::array`
- Arrays are fixed-size sequence containers: they hold a specific number of elements ordered in a strict linear sequence.
- 存的型態固定 Internally, an array does not keep any data other than the elements it contains (not even its size, which is a template parameter, fixed on compile time). 
- 一般使用的中括號就是 It is as efficient in terms of storage size as an ordinary array declared with the language's bracket syntax ([]). 
- 這邊只是多包了一層 This class merely adds a layer of member and global functions to it, so that arrays can be used as standard containers.
- 一次要到固定的記憶體空間不能改變大小 Unlike the other standard containers, arrays have a fixed size and do not manage the allocation of its elements through an allocator, they are an aggregate type encapsulating a fixed-size array of elements. Therefore, they cannot be expanded or contracted dynamically (see vector for a similar container that can be expanded).

**Memory**
- sizeof(T) * N
```cpp
template<typename T, std::size_t N>
class array {
    T elems[N];  // Fixed-size array
};
```

**Example Code**
- https://www.cplusplus.com/reference/array/array/
- https://en.cppreference.com/w/cpp/container/array
```cpp
#include <array>
const int SIZE = 5;
int arr[SIZE] = {1, 2, 3, 4, 5}; // Fixed-size array

// Access head, index, tail
int head = arr[0];       // head
int value = arr[2];      // index
int tail = arr[SIZE - 1]; // tail

// Size (Fixed in C++)
int size = SIZE; 

// Iterate
for (int i = 0; i < size; i++) {
std::cout << arr[i] << std::endl;
}

// Modify an element
arr[2] = 10; // Change value at index 2
```

-------------------------------------------------------

### 1.2 Vector `std::vector`
- Vectors are sequence containers representing arrays that can change in size.
- 既可以隨機存取又不會被綁住大小 Just like arrays, vectors use contiguous storage locations for their elements, which means that their elements can also be accessed using offsets on regular pointers to its elements, and just as efficiently as in arrays. But unlike arrays, their size can change dynamically, with their storage being handled automatically by the container.
- 因為是動態矩陣，當加入參數多到要重新擴大size時，全部複製出去是花時間的 Internally, vectors use a dynamically allocated array to store their elements. This array may need to be reallocated in order to grow in size when new elements are inserted, which implies allocating a new array and moving all elements to it. This is a relatively expensive task in terms of processing time, and thus, vectors do not reallocate each time an element is added to the container.
- 啥時要增大的策略可以自訂，amortized cost=O(n)/n=O(1)，所以append還是很便宜的 Instead, vector containers may allocate some extra storage to accommodate for possible growth, and thus the container may have an actual capacity greater than the storage strictly needed to contain its elements (i.e., its size). Libraries can implement different strategies for growth to balance between memory usage and reallocations, but in any case, reallocations should only happen at logarithmically growing intervals of size so that the insertion of individual elements at the end of the vector can be provided with amortized constant time complexity (see push_back).
- 比較 Therefore, compared to arrays, vectors consume more memory in exchange for the ability to manage storage and grow dynamically in an efficient way.
- 比較 Compared to the other dynamic sequence containers (deques, lists and forward_lists)
  - vectors are very efficient accessing its elements (just like arrays)
  - relatively efficient adding or removing elements from its end. 
  - For operations that involve inserting or removing elements at positions other than the end, they perform worse than the others
  - have less consistent iterators and references than lists and forward_lists.

**Use for**
* Simple storage
* Adding but not deleting
* Serialization
* Quick lookups by index
* Easy conversion to C-style arrays
* Efficient traversal (contiguous CPU caching)

**Do not use for**
* Insertion/deletion in the middle of the list
* Dynamically changing storage
* Non-integer indexing

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert Head  |          `O(n)` |
| Insert Index |          `O(n)` |
| Insert Tail  |          `O(1)` |
| Remove Head  |          `O(n)` |
| Remove Index |          `O(n)` |
| Remove Tail  |          `O(1)` |
| Find Index   |          `O(1)` |
| Find Object  |          `O(n)` |

**Memory**
- 24 bytes
```cpp
// std::vector<T>
template<typename T>
class vector {
    T* data;         // Pointer to dynamically allocated storage
    std::size_t size;      // Number of elements
    std::size_t capacity;  // Allocated capacity
};
```

**Example Code**
- https://cplusplus.com/reference/vector/vector/
- https://en.cppreference.com/w/cpp/container/vector
```cpp
#include <vector>
std::vector<int> v;

// Insert head, index, tail
v.insert(v.begin(), value);             // head
v.insert(v.begin() + index, value);     // index
v.push_back(value);                     // tail

// Access head, index, tail
int head = v.front();       // head
int value = v.at(index);    // index
int tail = v.back();        // tail

// Size
unsigned int size = v.size();

// Iterate
for(std::vector<int>::iterator it = v.begin(); it != v.end(); it++) {
    std::cout << *it << std::endl;
}

// Remove head, index, tail
v.erase(v.begin());             // head
v.erase(v.begin() + index);     // index
v.pop_back();                   // tail

// Clear
v.clear();
```

-------------------------------------------------------

### 1.3 Deque `std::deque`
- Double ended queue. deque (usually pronounced like "deck") is an irregular acronym of double-ended queue. Double-ended queues are sequence containers with dynamic sizes that can be expanded or contracted on both ends (either its front or its back).
- 通常是由動態矩陣實做的，可隨機存取(透過iter)，可頭尾變動大小 Specific libraries may implement deques in different ways, generally as some form of dynamic array. But in any case, they allow for the individual elements to be accessed directly through random access iterators, with storage handled automatically by expanding and contracting the container as needed.
- 雖然可插頭尾，但不保證記憶體存的順序連序 Therefore, they provide a functionality similar to vectors, but with efficient insertion and deletion of elements also at the beginning of the sequence, and not only at its end. But, unlike vectors, deques are not guaranteed to store all its elements in contiguous storage locations: accessing elements in a deque by offsetting a pointer to another element causes undefined behavior.
- 比較 For operations that involve frequent insertion or removals of elements at positions other than the beginning or the end, deques perform worse and have less consistent iterators and references than lists and forward lists.
- 比較 vectors and deques
  - provide a very similar interface and can be used for similar purposes, 
  - While vectors use a single array that needs to be occasionally reallocated for growth, the elements of a deque can be scattered in different chunks of storage, with the container keeping the necessary information internally to provide direct access to any of its elements in constant time and with a uniform sequential interface (through iterators). 
  - Therefore, deques are a little more complex internally than vectors, but this allows them to grow more efficiently under certain circumstances, especially with very long sequences, where reallocations become more expensive.
- https://www.cplusplus.com/reference/deque/deque/
- 實做 As opposed to std::vector, the elements of a deque are **not stored contiguously**: typical implementations use a sequence of **individually allocated fixed-size arrays**, with **additional bookkeeping**, which means indexed access to deque must perform **two pointer dereferences**, compared to vector's indexed access which performs only one.
- 實做 The storage of a deque is automatically expanded and contracted as needed. Expansion of a deque is **cheaper** than the expansion of a std::vector because it does **not involve copying** of the existing elements to a new memory location. On the other hand, deques typically have **large minimal memory cost**; a deque holding just **one element has to allocate its full internal array** (e.g. 8 times the object size on 64-bit libstdc++; 16 times the object size or 4096 bytes, whichever is larger, on 64-bit libc++).
- 可能的實作-動態二維陣列: https://www.ptt.cc/bbs/C_and_CPP/M.1316864705.A.D3F.html

**Notes**
* Pronounced 'deck'
* Stands for **D**ouble **E**nded **Que**ue

**Use for**
* Similar purpose of `std::vector`
* Basically `std::vector` with efficient `push_front` and `pop_front`

**Do not use for**
* C-style contiguous storage (not guaranteed)

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert Head  |          `O(1)` |
| Insert Index |          `O(n)` |
| Insert Tail  |          `O(1)` |
| Remove Head  |          `O(1)` |
| Remove Index |          `O(n)` |
| Remove Tail  |          `O(1)` |
| Find Index   |          `O(1)` |
| Find Object  |          `O(n)` |

**Memory**
- 40 bytes
```cpp
template<typename T>
class deque {
    T** map;               // Pointer to an array of block pointers
    std::size_t map_size;  // Number of block pointers
    std::size_t size;      // Number of elements
    std::size_t front_idx; // Index to the front element
    std::size_t back_idx;  // Index to the back element
};
```

**Example Code**
- https://cplusplus.com/reference/deque/deque/
- https://en.cppreference.com/w/cpp/container/deque
```cpp
#include <deque>
std::deque<int> d;

// Insert head, index, tail
d.push_front(value);                    // head
d.insert(d.begin() + index, value);     // index
d.push_back(value);                     // tail

// Access head, index, tail
int head = d.front();       // head
int value = d.at(index);    // index
int tail = d.back();        // tail

// Size
unsigned int size = d.size();

// Iterate
for(std::deque<int>::iterator it = d.begin(); it != d.end(); it++) {
    std::cout << *it << std::endl;
}

// Remove head, index, tail
d.pop_front();                  // head
d.erase(d.begin() + index);     // index
d.pop_back();                   // tail

// Clear
d.clear();
```

-------------------------------------------------------

### 1.4 Forward List `std::forward_list`
- Forward lists are sequence containers that allow constant time insert and erase operations anywhere within the sequence.
- 實做 Forward lists are implemented as singly-linked lists; Singly linked lists can store each of the elements they contain in different and unrelated storage locations. The ordering is kept by the association to each element of a link to the next element in the sequence.
- 比較 forward_list container and a list container. 
  - The first keeps internally only a link to the next element, while the latter keeps two links per element: one pointing to the next element and one to the preceding one, allowing efficient iteration in both directions
  - but consuming additional storage per element and with a slight higher time overhead inserting and removing elements.
  - forward list somewhat smaller and more efficient.
- 比較 Compared to other base standard sequence containers (array, vector and deque)
  - forward_list perform generally better in inserting, extracting and moving elements in any position within the container
  - therefore also in algorithms that make intensive use of these, like sorting algorithms.
- 比較 The main drawback of forward_lists and lists compared to these other sequence containers
  - they lack direct access to the elements by their position; takes linear time in the distance between these.
  - They also consume some extra memory to keep the linking information associated to each element (which may be an important factor for large lists of small-sized elements).
- member裡面沒有size，要花O(n)來求 The forward_list class template has been designed with efficiency in mind: By design, it is as efficient as a simple handwritten C-style singly-linked list, and in fact is the only standard container to deliberately lack a size member function for efficiency considerations: due to its nature as a linked list, having a size member that takes constant time would require it to keep an internal counter for its size (as list does). 
  - This would consume some extra storage and make insertion and removal operations slightly less efficient. 
  - To obtain the size of a forward_list object, you can use the distance algorithm with its begin and end, which is an operation that takes linear time.

**Example Code**
- https://www.cplusplus.com/reference/forward_list/forward_list/
- https://en.cppreference.com/w/cpp/container/forward_list
```cpp
#include <forward_list>
std::forward_list<int> fl;

// Insert
fl.push_front(value);                      // Head
auto it = fl.before_begin();
std::advance(it, index);                   
fl.insert_after(it, value);                // Index
fl.insert_after(fl.before_begin(), value); // Tail (No push_back)

// Access
int head = fl.front();
auto index_it = fl.begin();
std::advance(index_it, index);
int value = *index_it;

// Iterate
for (int v : fl) std::cout << v << std::endl;

// Remove
fl.pop_front();            // Head
std::advance(it, index);
fl.erase_after(it);        // Index
fl.reverse(); fl.pop_front(); fl.reverse(); // Tail workaround

// Clear
fl.clear();

// Additional operations
fl.remove(value); // Remove by value
fl.unique();      // Remove duplicates
fl.sort();        // Sort (C++17+)
fl.reverse();     // Reverse

std::forward_list<int> fl2 = {6, 7, 8};
fl.merge(fl2);    // Merge two sorted lists
```

-------------------------------------------------------

### 1.5 List `std::list`
- Lists are sequence containers that allow constant time insert and erase operations anywhere within the sequence, and iteration in both directions.
- List containers are implemented as doubly-linked lists; Doubly linked lists can store each of the elements they contain in different and unrelated storage locations. Thehttps://www.cplusplus.com/reference/stack/stack/ ordering is kept internally by the association to each element of a link to the element preceding it and a link to the element following it.
- https://www.cplusplus.com/reference/list/list/

**Use for**
* Insertion into the middle/beginning of the list
* Efficient sorting (pointer swap vs. copying)

**Do not use for**
* Direct access

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert Head  |          `O(1)` |
| Insert Index |          `O(n)` |
| Insert Tail  |          `O(1)` |
| Remove Head  |          `O(1)` |
| Remove Index |          `O(n)` |
| Remove Tail  |          `O(1)` |
| Find Index   |          `O(n)` |
| Find Object  |          `O(n)` |

**Example Code**
- https://cplusplus.com/reference/list/list/
- https://en.cppreference.com/w/cpp/container/list
```cpp
#include <list>
std::list<int> l;

// Insert head, index, tail
l.push_front(value);                    // head
l.insert(l.begin() + index, value);     // index
l.push_back(value);                     // tail

// Access head, index, tail
int head = l.front();                                           // head
int value = std::next(l.begin(), index);		        // index
int tail = l.back();                                            // tail

// Size
unsigned int size = l.size();

// Iterate
for(std::list<int>::iterator it = l.begin(); it != l.end(); it++) {
    std::cout << *it << std::endl;
}

// Remove head, index, tail
l.pop_front();                  // head
l.erase(l.begin() + index);     // index
l.pop_back();                   // tail

// Clear
l.clear();

// Splice: Transfer elements from list to list
//	splice(iterator pos, list &x)
//  	splice(iterator pos, list &x, iterator i)
//  	splice(iterator pos, list &x, iterator first, iterator last)
l.splice(l.begin() + index, list2);

// Remove: Remove an element by value
l.remove(value);

// Unique: Remove duplicates
l.unique();

// Merge: Merge two sorted lists
l.merge(list2);

// Sort: Sort the list
l.sort();

// Reverse: Reverse the list order
l.reverse();
```

-------------------------------------------------------

### 1.6 Stack `std::stack`
- Stacks are a type of container adaptor, specifically designed to operate in a LIFO context (last-in first-out), where elements are inserted and extracted only from one end of the container.
- stacks are implemented as container adaptors, which are classes that use an encapsulated object of a specific container class as its underlying container, providing a specific set of member functions to access its elements. Elements are pushed/popped from the "back" of the specific container, which is known as the top of the stack.
- The underlying container may be any of the standard container class templates or some other specifically designed container class. The container shall support the following operations: 
   - empty
   - size
   - back
   - push_back
   - pop_back
- The standard container classes `vector, deque, list and forward list` fulfill these requirements. 
- By default, if no container class is specified for a particular stack class instantiation, the standard container `deque` is used.

**Use for**
* First-In Last-Out operations
* Reversal of elements

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Push         |          `O(1)` |
| Pop          |          `O(1)` |
| Top          |          `O(1)` |

**Example Code**
- https://www.cplusplus.com/reference/stack/stack/
- https://en.cppreference.com/w/cpp/container/stack
```cpp
#include <stack>
std::stack<int> s;

// Push
s.push(20);

// Size
unsigned int size = s.size();

// Pop
s.pop();

// Top
int top = s.top();
```

-------------------------------------------------------

### 1.7 Queue `std::queue`
- queues are a type of container adaptor, specifically designed to operate in a FIFO context (first-in first-out), where elements are inserted into one end of the container and extracted from the other.
- queues are implemented as containers adaptors, which are classes that use an encapsulated object of a specific container class as its underlying container, providing a specific set of member functions to access its elements. Elements are pushed into the "back" of the specific container and popped from its "front".
- The underlying container may be one of the standard container class template or some other specifically designed container class. This underlying container shall support at least the following operations:
  - empty
  - size
  - front
  - back
  - push_back
  - pop_front
- The standard container classes `deque and list` fulfill these requirements. 因為需要拿到頭和尾的值在O(1)內，所以必須是雙向linked list把dummy接到頭尾才有可能
- By default, if no container class is specified for a particular queue class instantiation, the standard container `deque` is used.
- https://www.cplusplus.com/reference/queue/queue/

**Use for**
* First-In First-Out operations
* Ex: Simple online ordering system (first come first served)
* Ex: Semaphore queue handling
* Ex: CPU scheduling (FCFS)

**Notes**
* Often implemented as a `std::deque`

**Example Code**
- https://en.cppreference.com/w/cpp/container/queue
- https://cplusplus.com/reference/queue/queue/
```cpp
#include <queue>
std::queue<int> q;

// Insert
q.push(value);

// Access head, tail
int head = q.front();       // head
int tail = q.back();        // tail

// Size
unsigned int size = q.size();

// Remove
q.pop();
```

-------------------------------------------------------

### 1.8 Priority Queue `std::priority_queue` Heap
- Priority queues are a type of container adaptors, specifically designed such that its first element is always the greatest of the elements it contains, according to some strict weak ordering criterion.
- This context is similar to a heap, where elements can be inserted at any moment, and only the max heap element can be retrieved (the one at the top in the priority queue).
- Priority queues are implemented as container adaptors, which are classes that use an encapsulated object of a specific container class as its underlying container, providing a specific set of member functions to access its elements. Elements are popped from the "back" of the specific container, which is known as the top of the priority queue.
- The underlying container may be any of the standard container class templates or some other specifically designed container class. The container shall be accessible through `random access iterators` and support the following operations:
  - empty()
  - size()
  - front()
  - push_back()
  - pop_back()
- The standard container classes `vector and deque` fulfill these requirements(especially Randomly Access). Implementation in Array, Indexing start from 1; `Find Parent = floor(i/2); Find Left Child = 2i; Right Child 2i+1`.
- By default, if no container class is specified for a particular priority_queue class instantiation, the standard container `vector` is used.
- Support of random access iterators is required to keep a heap structure internally at all times. This is done automatically by the container adaptor by automatically calling the algorithm functions `make_heap, push_heap and pop_heap` when needed. (Templete including Type, Container, Compare) 內部不是sorted的，只是維持heap特性，另外隨機存取是留給那些維持heap功能的用的，對外不開放iterate over它
  - min heap: priority_queue<int, vector<int>, greater<int> > gquiz; // Sorted heap in increasing
  - max heap: priority_queue<int> gquiz; // Sorted heap in non-increasing
- https://www.cplusplus.com/reference/queue/priority_queue/

**Use for**
* First-In First-Out operations where **priority** overrides arrival time
* Ex: CPU scheduling (smallest job first, system/user priority)
* Ex: Medical emergencies (gunshot wound vs. broken arm)

**Notes**
* Often implemented as a `std::vector`

**Example Code**
- https://en.cppreference.com/w/cpp/container/priority_queue
- https://cplusplus.com/reference/queue/priority_queue/
```cpp
#include <priority_queue>
std::priority_queue<int> p;

// Insert
p.push(value);

// Access
int top = p.top();  // 'Top' element

// Size
unsigned int size = p.size();

// Remove
p.pop();
```

-------------------------------------------------------

### 1.9 Set `std::set` Binary Tree
- Sets are containers that store unique elements following a specific order.
- key=val且不重複 In a set, the value of an element also identifies it (the value is itself the key, of type T), and each value must be unique. The value of the elements in a set cannot be modified once in the container (the elements are always const), but they can be inserted or removed from the container.
- 排序好的 Internally, the elements in a set are always sorted following a specific strict weak ordering criterion indicated by its internal comparison object (of type Compare).
- 直接index會比較慢，但有照順序牌所以iterate會比較快 set containers are generally slower than unordered_set containers to access individual elements by their key, but they allow the direct iteration on subsets based on their order.
- 實做 Sets are typically implemented as binary search trees.

**Use for**
* Removing duplicates
* Ordered dynamic storage

**Do not use for**
* Simple storage
* Direct access by index

**Notes**
* Sets are often implemented with binary search trees

**Time Complexity**

| Operation    | Time Complexity |
|--------------|-----------------|
| Insert       |     `O(log(n))` |
| Remove       |     `O(log(n))` |
| Find         |     `O(log(n))` |

**Example Code**
- https://www.cplusplus.com/reference/set/set/
- https://en.cppreference.com/w/cpp/container/set
```cpp
#include <set>
std::set<int> s;

// Insert
s.insert(20);

// Size
unsigned int size = s.size();

// Iterate
for(std::set<int>::iterator it = s.begin(); it != s.end(); it++) {
    std::cout << *it << std::endl;
}

// Remove
s.erase(20);

// Clear
s.clear();

// Find if an element exists
bool exists = (s.find(20) != s.end());

// Count the number of elements with a certain value
unsigned int count = s.count(20);
```

-------------------------------------------------------

### 1.10 Multiset `std::multiset`
- Multisets are containers that store elements following a specific order, and where multiple elements can have equivalent values.
- key=val且可重複 In a multiset, the value of an element also identifies it (the value is itself the key, of type T). The value of the elements in a multiset cannot be modified once in the container (the elements are always const), but they can be inserted or removed from the container.
- 排序好的 Internally, the elements in a multiset are always sorted following a specific strict weak ordering criterion indicated by its internal comparison object (of type Compare).
- 直接index會比較慢，但有照順序牌所以iterate會比較快 multiset containers are generally slower than unordered_multiset containers to access individual elements by their key, but they allow the direct iteration on subsets based on their order.
- 實做 Multisets are typically implemented as binary search trees.

**Example Code**
- https://www.cplusplus.com/reference/set/multiset/
- https://en.cppreference.com/w/cpp/container/multiset
```cpp
#include <set>
std::multiset<int> ms;

// Insert
ms.insert(value);   // Inserts element (allows duplicates)

// Access (multiset has no direct index access)
int first = *ms.begin();  // Smallest element
int last = *ms.rbegin();  // Largest element

// Iterate
for (int v : ms) std::cout << v << std::endl;

// Count occurrences
int count = ms.count(value);

// Remove
ms.erase(value);      // Remove all occurrences of value
ms.erase(ms.begin()); // Remove smallest element
ms.clear();           // Clear all elements

// Additional operations
auto it = ms.find(value);  // Find first occurrence
if (it != ms.end()) ms.erase(it); // Remove only one occurrence

std::multiset<int> ms2 = {5, 6, 7};
ms.merge(ms2); // Merge two multisets
```

-------------------------------------------------------

### 1.11 Map `std::map` Binary Tree
- Maps are associative containers that store elements formed by a combination of a key value and a mapped value, following a specific order.
- key val pairs對. In a map, the key values are generally used to sort and uniquely identify the elements, while the mapped values store the content associated to this key. The types of key and mapped value may differ, and are grouped together in member type value_type, which is a pair type combining both: ```typedef pair<const Key, T> value_type;```
- 按照Key排序好 Internally, the elements in a map are always sorted by its key following a specific strict weak ordering criterion indicated by its internal comparison object (of type Compare).
- 直接index會比較慢，但有照順序牌所以iterate會比較快. map containers are generally slower than unordered_map containers to access individual elements by their key, but they allow the direct iteration on subsets based on their order.
- 隨機存取 The mapped values in a map can be accessed directly by their corresponding key using the `bracket operator ((operator[]).`
- 實做 Maps are typically implemented as binary search trees.

**Use for**
* Key-value pairs
* Constant lookups by key
* Searching if key/value exists
* Removing duplicates
* `std::map`
    * Ordered map
* `std::unordered_map`
    * Hash table

**Do not use for**
* Sorting

**Notes**
* Typically ordered maps (`std::map`) are slower than unordered maps (`std::unordered_map`)
* Maps are typically implemented as *binary search trees*

**Time Complexity**

**Time Complexity**

| Operation           | Time Complexity |
|---------------------|-----------------|
| Insert              |     `O(log(n))` |
| Access by Key       |     `O(log(n))` |
| Remove by Key       |     `O(log(n))` |
| Find/Remove Value   |     `O(log(n))` |


- Insert v.s. Emplace v.s Operator[]
  - emplace: This new element is constructed in place using args as the arguments for the construction of a value_type (which is an object of a pair type).
  - insert: which either copies or moves existing objects into the container.
  - operator[]: is a find-or-add operator. It will try to find an element with the given key inside the map, and if it exists it will return a reference to the stored value. If it does not, it will create a new element inserted in place with default initialization and return a reference to it.
  - insert: (in the single element flavor) takes a value_type (std::pair<const Key,Value>), it uses the key (first member) and tries to insert it. Because std::map does not allow for duplicates if there is an existing element it will not insert anything. Inserts a new element in the map if its key is unique.

**Example Code**
- https://www.cplusplus.com/reference/map/map/
- https://en.cppreference.com/w/cpp/container/map
```cpp
#include <map>
std::map<std::string, std::string> m;

// Insert
m.insert(std::pair<std::string, std::string>("key", "value"));

// Access by key
std::string value = m.at("key");

// Size
unsigned int size = m.size();

// Iterate
for(std::map<std::string, std::string>::iterator it = m.begin(); it != m.end(); it++) {
    std::cout << *it << std::endl;
}

// Remove by key
m.erase("key");

// Clear
m.clear();

// Find if an element exists by key
bool exists = (m.find("key") != m.end());

// Count the number of elements with a certain key
unsigned int count = m.count("key");
```

-------------------------------------------------------

### 1.12 Multimap `std::multimap`
- Multimaps are associative containers that store elements formed by a combination of a key value and a mapped value, following a specific order, and where multiple elements can have equivalent keys.
- In a multimap, the key values are generally used to sort and uniquely identify the elements, while the mapped values store the content associated to this key. The types of key and mapped value may differ, and are grouped together in member type value_type, which is a pair type combining both: `typedef pair<const Key, T> value_type;`
- Internally, the elements in a multimap are always sorted by its key following a specific strict weak ordering criterion indicated by its internal comparison object (of type Compare).
- multimap containers are generally slower than unordered_multimap containers to access individual elements by their key, but they allow the direct iteration on subsets based on their order.
- Multimaps are typically implemented as binary search trees.

**Example Code**
- https://www.cplusplus.com/reference/map/multimap/
- https://en.cppreference.com/w/cpp/container/multimap
```cpp
#include <map>
std::multimap<int, std::string> mm;

// Insert
mm.insert({1, "Apple"});
mm.insert({2, "Banana"});
mm.insert({1, "Avocado"}); // Allows duplicate keys

// Access
auto range = mm.equal_range(1); // Get all values for key 1
for (auto it = range.first; it != range.second; ++it) {
    std::cout << it->first << " -> " << it->second << std::endl;
}

// Iterate
for (const auto& [key, value] : mm) {
    std::cout << key << " -> " << value << std::endl;
}

// Count occurrences of a key
int count = mm.count(1);

// Remove
mm.erase(1);  // Remove all pairs with key 1
auto it = mm.find(2);
if (it != mm.end()) mm.erase(it); // Remove only one pair

// Clear
mm.clear();

// Additional operations
std::multimap<int, std::string> mm2 = {{3, "Cherry"}, {4, "Dates"}};
mm.merge(mm2); // Merge two multimaps
```

-------------------------------------------------------

### 1.13 Unordered Set `std::unordered_set` Hash table/map
- Unordered sets are containers that store unique elements in no particular order, and which allow for fast retrieval of individual elements based on their value.
- In an unordered_set, the value of an element is at the same time its key, that identifies it uniquely. Keys are immutable, therefore, the elements in an unordered_set cannot be modified once in the container - they can be inserted and removed, though.
- 無序 Internally, the elements in the unordered_set are not sorted in any particular order, but organized into buckets depending on their hash values to allow for fast access to individual elements directly by their values (with a constant average time complexity on average).
- 快速存取，遊走慢 unordered_set containers are faster than set containers to access individual elements by their key, although they are generally less efficient for range iteration through a subset of their elements.
- Iterators in the container are at least forward iterators.

**Time Complexity**

| Operation           | Time Complexity |
|---------------------|-----------------|
| Insert              |          `O(1)` |
| Access by Key       |          `O(1)` |
| Remove by Key       |          `O(1)` |
| Find/Remove Value   |              -- |

**Example Code**
- https://www.cplusplus.com/reference/unordered_set/unordered_set/
- https://en.cppreference.com/w/cpp/container/unordered_set
```cpp
#include <unordered_set>
std::unordered_set<int> us;

// Insert
us.insert(10);
us.insert(20);
us.insert(10); // Duplicate ignored

// Access (No direct index, only find)
if (us.find(10) != us.end()) std::cout << "Found 10\n";

// Iterate (unordered)
for (int v : us) std::cout << v << std::endl;

// Count occurrences
int count = us.count(10); // 0 or 1 (since no duplicates allowed)

// Remove
us.erase(10);  // Remove element
us.clear();    // Clear all elements

// Additional operations
std::unordered_set<int> us2 = {30, 40, 50};
us.merge(us2); // Merge two sets
```

-------------------------------------------------------

### 1.14 Unordered Multiset `std::unordered_multiset`
- Unordered multisets are containers that store elements in no particular order, allowing fast retrieval of individual elements based on their value, much like unordered_set containers, but allowing different elements to have equivalent values.
- In an unordered_multiset, the value of an element is at the same time its key, used to identify it. Keys are immutable, therefore, the elements in an unordered_multiset cannot be modified once in the container - they can be inserted and removed, though.
- Internally, the elements in the unordered_multiset are not sorted in any particular, but organized into buckets depending on their hash values to allow for fast access to individual elements directly by their values (with a constant average time complexity on average).
- 相同的會存在一起 Elements with equivalent values are grouped together in the same bucket and in such a way that an iterator (see equal_range) can iterate through all of them.
- Iterators in the container are at least forward iterators.
- Notice that this container is not defined in its own header, but shares header <unordered_set> with unordered_set.

**Example Code**
- https://www.cplusplus.com/reference/unordered_set/unordered_multiset/
- https://en.cppreference.com/w/cpp/container/unordered_multiset
```cpp
#include <unordered_multiset>
std::unordered_multiset<int> ums;

// Insert (allows duplicates)
ums.insert(10);
ums.insert(20);
ums.insert(10); // Duplicate allowed

// Access (no direct index, only find)
if (ums.find(10) != ums.end()) std::cout << "Found 10\n";

// Iterate (unordered)
for (int v : ums) std::cout << v << std::endl;

// Count occurrences
int count = ums.count(10); // Returns the number of occurrences

// Remove
ums.erase(10);  // Removes all occurrences of 10
auto it = ums.find(20);
if (it != ums.end()) ums.erase(it); // Remove only one occurrence

// Clear
ums.clear();

// Additional operations
std::unordered_multiset<int> ums2 = {30, 40, 50};
ums.merge(ums2); // Merge two multisets
```

-------------------------------------------------------

### 1.15 Unordered Map `std::unordered_map` Hash table/map
- Unordered maps are associative containers that store elements formed by the combination of a key value and a mapped value, and which allows for fast retrieval of individual elements based on their keys.
- In an unordered_map, the key value is generally used to uniquely identify the element, while the mapped value is an object with the content associated to this key. Types of key and mapped value may differ.
- Internally, the elements in the unordered_map are not sorted in any particular order with respect to either their key or mapped values, but organized into buckets depending on their hash values to allow for fast access to individual elements directly by their key values (with a constant average time complexity on average).
- unordered_map containers are faster than map containers to access individual elements by their key, although they are generally less efficient for range iteration through a subset of their elements.
- Unordered maps implement the direct access operator (operator[]) which allows for direct access of the mapped value using its key value as argument.
- Iterators in the container are at least forward iterators.

**Example Code**
- https://www.cplusplus.com/reference/unordered_map/unordered_map/
- https://en.cppreference.com/w/cpp/container/unordered_map
```cpp
#include <unordered_map>
std::unordered_map<int, std::string> um;

// Insert
um.insert({1, "Apple"});
um[2] = "Banana";
um[1] = "Avocado"; // Overwrites existing key

// Access
std::cout << um[1] << std::endl;        // Access by key (creates default if not found)
std::cout << um.at(2) << std::endl;     // Access by key (throws exception if not found)

// Iterate (unordered)
for (const auto& [key, value] : um) {
    std::cout << key << " -> " << value << std::endl;
}

// Check existence
if (um.find(1) != um.end()) std::cout << "Key 1 found\n";

// Size
std::cout << "Size: " << um.size() << std::endl;

// Remove
um.erase(1);  // Remove by key
um.clear();   // Clear all elements

// Additional operations
std::unordered_map<int, std::string> um2 = {{3, "Cherry"}, {4, "Dates"}};
um.merge(um2); // Merge two maps
```

-------------------------------------------------------

### 1.16 Unordered Multimap `std::unordered_multimap`
- Unordered multimaps are associative containers that store elements formed by the combination of a key value and a mapped value, much like unordered_map containers, but allowing different elements to have equivalent keys.
- In an unordered_multimap, the key value is generally used to uniquely identify the element, while the mapped value is an object with the content associated to this key. Types of key and mapped value may differ.
- Internally, the elements in the unordered_multimap are not sorted in any particular order with respect to either their key or mapped values, but organized into buckets depending on their hash values to allow for fast access to individual elements directly by their key values (with a constant average time complexity on average).
- Elements with equivalent keys are grouped together in the same bucket and in such a way that an iterator (see equal_range) can iterate through all of them.
- Iterators in the container are at least forward iterators.
- Notice that this container is not defined in its own header, but shares header <unordered_map> with unordered_map.

**Example Code**
- https://www.cplusplus.com/reference/unordered_map/unordered_multimap/
- https://en.cppreference.com/w/cpp/container/unordered_multimap
```cpp
#include <unordered_multimap>
std::unordered_multimap<int, std::string> umm;

// Insert (allows duplicate keys)
umm.insert({1, "Apple"});
umm.insert({2, "Banana"});
umm.insert({1, "Avocado"}); // Duplicate key allowed

// Access (get all values for a key)
auto range = umm.equal_range(1);
for (auto it = range.first; it != range.second; ++it) {
    std::cout << it->first << " -> " << it->second << std::endl;
}

// Iterate (unordered)
for (const auto& [key, value] : umm) {
    std::cout << key << " -> " << value << std::endl;
}

// Count occurrences of a key
int count = umm.count(1);

// Remove
umm.erase(1);  // Remove all pairs with key 1
auto it = umm.find(2);
if (it != umm.end()) umm.erase(it); // Remove only one pair

// Clear
umm.clear();

// Additional operations
std::unordered_multimap<int, std::string> umm2 = {{3, "Cherry"}, {4, "Dates"}};
umm.merge(umm2); // Merge two multimaps (C++17+)
```

-------------------------------------------------------

## 2. Trees
### 2.0 Heap
* A heap is essentially an instance of a priority queue
* A **min** heap is structured with the root node as the smallest and each child subsequently larger than its parent
* A **max** heap is structured with the root node as the largest and each child subsequently smaller than its parent
* A min heap could be used for *Smallest Job First* CPU Scheduling
* A max heap could be used for *Priority* CPU Scheduling

**Max Heap Example (using a binary tree)**  
<img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/General/MaxHeap.png"/>

-------------------------------------------------------

### 2.1 Binary Tree
* A binary tree is a tree with at most two (2) child nodes per parent
* Binary trees are commonly used for implementing `O(log(n))` operations for ordered maps, sets, heaps, and binary search trees
* Binary trees are **sorted** in that nodes with values greater than their parents are inserted to the **right**, while nodes with values less than their parents are inserted to the **left**

**Binary Search Tree**   
<img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/General/BinarySearchTree.png"/>
```
        1
       / \
      2   3
     / \   \
    4   5   6
```

- Pre-Order traversal: 1, 2, 4, 5, 3, 6
```
PreOrderTraversal(node):
    if node is not null:
        visit(node)
        PreOrderTraversal(node.left)
        PreOrderTraversal(node.right)
```
- In-Order traversal: 4, 2, 5, 1, 3, 6
```
InOrderTraversal(node):
    if node is not null:
        InOrderTraversal(node.left)
        visit(node)
        InOrderTraversal(node.right)
```
- Post-Order traversal: 4, 5, 2, 6, 3, 1
```
PostOrderTraversal(node):
    if node is not null:
        PostOrderTraversal(node.left)
        PostOrderTraversal(node.right)
        visit(node)

```
- Level-Order traversal: 1, 2, 3, 4, 5, 6
```
LevelOrderTraversal(root):
    queue = new Queue()
    queue.enqueue(root)
    
    while queue is not empty:
        node = queue.dequeue()
        visit(node)
        if node.left is not null:
            queue.enqueue(node.left)
        if node.right is not null:
            queue.enqueue(node.right)
```
- ![圖片](https://github.com/user-attachments/assets/dde00558-ba19-4fcb-8ef7-8c6ac7ca1c70)

-------------------------------------------------------

### 2.2 Balanced Trees
* Balanced trees are a special type of tree which maintains its balance to ensure `O(log(n))` operations
* When trees are not balanced the benefit of `log(n)` operations is lost due to the highly vertical structure
* Examples of balanced trees:
    * AVL Trees
    * Red-Black Trees

-------------------------------------------------------

## 3. NP Complete Problems
### 3.1 Complexity Classes
- The class P:
  - class of problems that can be solved in polynomial time
  - closed under addition, multiplication, composition, complement(logical not) 仍會可解
- The class NP: (nondeterministic polynomial time)
  - class of problems that can be verified in polynomial time 
  - 目前已知是P的話一定是NP，但NP會不會一定是P就不知道了(見文氏圖)
- The class NP-complete:
  - problems can be *verified* in polynomial time, but not *solved*. 本身是NP
  - it can be used to simulate any other problem with similar solvability. 可以分解轉換成不同問題in polynomial time，而且那些問題也是NP
- The class NP-hard:
  - it can be used to simulate any other problem with similar solvability. 可以分解轉換成不同問題in polynomial time

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/P_np_np-complete_np-hard.svg/1280px-P_np_np-complete_np-hard.svg.png" width=500>

-------------------------------------------------------

### 3.2 Traveling Salesman Problem (TSP)
**Definition**  
* A salesman must visit **N** cities exactly once and return to the starting city while minimizing total travel cost (distance/time).  
* Formally: Find a tour that minimizes  
```
  \sum D(c_i, c_{i+1}) + D(c_N, c_1)
```

**Types of TSP**  
* **Symmetric TSP (STSP):** \( D(i, j) = D(j, i) \) (e.g., road networks).  
* **Asymmetric TSP (ATSP):** \( D(i, j) \neq D(j, i) \) (e.g., flight routes).  
* **Multiple TSP (mTSP):** Multiple salesmen.  
* **TSP with Time Windows (TSPTW):** Visit cities within time constraints.  

**Complexity**  
* **NP-hard problem** → No known polynomial-time solution.  
* Exact solutions are computationally expensive for large N.  

**Solving Methods: Exact (Optimal, Slow)**  
* **Brute Force:** \( O(N!) \) – Too slow.  
* **Dynamic Programming (Held-Karp):** \( O(N^2 2^N) \).  
* **Integer Linear Programming (ILP):** Uses solvers like CPLEX.  

**Solving Methods: Approximate (Fast, Not Always Optimal)**  
* **Nearest Neighbor:** Greedy, fast but suboptimal.  
* **Christofides Algorithm:** At most **1.5×** optimal (for STSP).  
* **Metaheuristics:** Simulated Annealing, Genetic Algorithms, Ant Colony Optimization, Tabu Search.  

**Applications**  
* **Logistics & Delivery** (e.g., route planning).  
* **Manufacturing** (e.g., PCB drilling sequences).  
* **Robotics** (e.g., AGV path planning).  
* **Genomics** (e.g., DNA sequencing).  

-------------------------------------------------------

### 3.3 Knapsack Problem
- 小偷要偷物品，但包包容量有限，怎樣才能偷到最多價值，給物品的大小list和物品的價值list
- Fractional Knapsack
  - greedy algorithm 解，只要把價值array和物品大小array相除O(n)，然後sort這個cp值array O(nlgn)，然後從最高的開始取配合物品大小array O(n)，總的會花O(nlgn)
- 0-1 Knapsack 
  - NP-complete
  - O(nW) pseudo polynomial time
  - https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/
```c++
// DP with top down
// Time Complexity: O(2^n): As there are redundant subproblems.
// Auxiliary Space :O(1): As no extra data structure has been used for storing values.
int knapSack(int W, int wt[], int val[], int n)
{
 
    // Base Case
    if (n == 0 || W == 0)
        return 0;
 
    // If weight of the nth item is more
    // than Knapsack capacity W, then
    // this item cannot be included
    // in the optimal solution
    if (wt[n - 1] > W)
        return knapSack(W, wt, val, n - 1);
 
    // Return the maximum of two cases:
    // (1) nth item included
    // (2) not included
    else
        return max(
            val[n - 1]
                + knapSack(W - wt[n - 1], 
                           wt, val, n - 1),
            knapSack(W, wt, val, n - 1));
}
```
```c++
// DP with bottom up
// Time Complexity: O(N*W): where ‘N’ is the number of weight element and ‘W’ is capacity. As for every weight element we traverse through all weight capacities 1<=w<=W.
// Auxiliary Space: O(N*W): The use of 2-D array of size ‘N*W’.
int knapSack(int W, int wt[], int val[], int n)
{
    int i, w;
    int K[n + 1][W + 1];
 
    // Build table K[][] in bottom up manner
    for (i = 0; i <= n; i++) 
    {
        for (w = 0; w <= W; w++) 
        {
            if (i == 0 || w == 0)
                K[i][w] = 0;
            else if (wt[i - 1] <= w)
                K[i][w] = max(val[i - 1]
                          + K[i - 1][w - wt[i - 1]],
                          K[i - 1][w]);
            else
                K[i][w] = K[i - 1][w];
        }
    }
 
    return K[n][W];
}
```
```c++
// DP with top down memoization
// Time Complexity: O(N*W). As redundant calculations of states are avoided.
// Auxiliary Space: O(N*W). The use of 2D array data structure for storing intermediate states-:
int knapSackRec(int W, int wt[], 
                int val[], int i,
                int** dp) {
    // base condition
    if (i < 0)
        return 0;
    if (dp[i][W] != -1)
        return dp[i][W];
 
    if (wt[i] > W) {
 
        // Store the value of function call
        // stack in table before return
        dp[i][W] = knapSackRec(W, wt, 
                               val, i - 1, 
                               dp);
        return dp[i][W];
    }
    else {
        // Store value in a table before return
        dp[i][W] = max(val[i]
                      + knapSackRec(W - wt[i], 
                                   wt, val,
                                   i - 1, dp),
                       knapSackRec(W, wt, val, 
                                   i - 1, dp));
 
        // Return value of table after storing
        return dp[i][W];
    }
}
int knapSack(int W, int wt[], int val[], int n) {
    // double pointer to declare the
    // table dynamically
    int** dp;
    dp = new int*[n];
 
    // loop to create the table dynamically
    for (int i = 0; i < n; i++)
        dp[i] = new int[W + 1];
 
    // loop to initially filled the
    // table with -1
    for (int i = 0; i < n; i++)
        for (int j = 0; j < W + 1; j++)
            dp[i][j] = -1;
    return knapSackRec(W, wt, val, n - 1, dp);
}
```

-------------------------------------------------------

## 4. Algorithms
###  4.1 Insertion Sort
**Idea** 撲克牌式整理 把牌插到適合的位置
1. Iterate over all elements
2. For each element:
    * Check if element is larger than largest value in sorted array
3. If larger: Move on
4. If smaller: Move item to correct position in sorted array

**Details**
* **Data structure:** Array
* **Space:** `O(1)`
* **Best Case:** Already sorted, `O(n)`
* **Worst Case:** Reverse sorted, `O(n^2)`
* **Average:** `O(n^2)`

**Advantages**
* Easy to code
* Intuitive
* Better than selection sort and bubble sort for small data sets
* Can sort in-place

**Disadvantages**
* Very inefficient for large datasets

**Visualization**
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Sorting/Animations/Insertion%20Sort.gif"/>
```c++
InsertionSort(A){
	for(j=1 to A.length-1){
		key = A[j];
		i = j-1;
		while (i>=0 && A[i]>key){
			A[i+1] = A[i];
			i--;
		}
		A[i+1] = key;
	}
}
```

-------------------------------------------------------

### 4.2 Selection Sort
**Idea** 按部就班 把最小的一直往左送
1. Iterate over all elements
2. For each element:
    * If smallest element of unsorted sublist, swap with left-most unsorted element

**Details**
* **Data structure:** Array
* **Space:** `O(1)`
* **Best Case:** Already sorted, `O(n^2)`
* **Worst Case:** Reverse sorted, `O(n^2)`
* **Average:** `O(n^2)`

**Advantages**
* Simple
* Can sort in-place
* Low memory usage for small datasets

**Disadvantages**
* Very inefficient for large datasets

**Visualization**
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Sorting/Animations/Selection%20Sort.gif"/>
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Sorting/Animations/Selection%20Sort%202.gif"/>
```c++
SelectionSort(A){
	for(i=0 to A.length-2){
		now = A[i], min=now;
		for(i=j+1 to A.length-1)
			if (A[j]<min) min = A[j];
		swap(now, min)
	}
}
```

-------------------------------------------------------

### 4.3 Bubble Sort
**Idea** 如果順序不對，相鄰的兩個就交換，一直重複從頭刷到尾直到不用交換
1. Iterate over all elements
2. For each element:
    * Swap with next element if out of order
3. Repeat until no swaps needed

**Details**
* **Data structure:** Array
* **Space:** `O(1)`
* **Best Case:** Already sorted `O(n)`
* **Worst Case:** Reverse sorted, `O(n^2)`
* **Average:** `O(n^2)`

**Advantages**
* Easy to detect if list is sorted

**Disadvantages**
* Very inefficient for large datasets
* Much worse than even insertion sort

**Visualization**
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Sorting/Animations/Bubble%20Sort.gif"/>
```c++
BubbleSort(A){
	sorted = false;
	while (!sorted){ //也可以用for 1~N 次
		sorted = true;
		for(i=0 to A.length-2){
			if (A[i+1]<A[i]) swap(A[i+1], A[i]);
			sorted = false;
		}
	}
}
```

-------------------------------------------------------

### 4.4 Merge Sort
**Idea** (Divide and Conquer, 在Merge的時候sort花O(n))
1. Divide list into smallest unit (1 element)
2. Compare each element with the adjacent list
3. Merge the two adjacent lists
4. Repeat

**Details**
* **Complexity:** T(n) = 2T(n/2) + O(n)
* **Data structure:** Array
* **Space:** `O(n) auxiliary`
* **Best Case:** `O(nlog(n))`
* **Worst Case:** Reverse sorted, `O(nlog(n))`
* **Average:** `O(nlog(n))`

**Advantages**
* High efficiency on large datasets
* Nearly always O(nlog(n))
* Can be parallelized
* Better space complexity than standard Quicksort

**Disadvantages**
* Still requires O(n) extra space
* Slightly worse than Quicksort in some instances

**Visualization**
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Sorting/Animations/Merge%20Sort.gif"/>
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Sorting/Animations/Merge%20Sort%202.gif"/>
```c++
MergeSort(A, p, r){
	if (p<r){
		q = (p+r)/2;
		MergeSort(A, p, q);
		MergeSort(A, q+1, r);
		Merge(A, p, q, r);	
	}
}
Merge(A, p, q, r){
	n1 = q-p+1, n2 = r-q;
	create array L[n1+1], R[n2+1]
	for (i=0 to n1-1) A[i+p] = L[i];
	for (j=0 to n2-1) A[j+q+1] = R[j];
	i = 0, j=0, L[n1]=MAX, L[n2]=MAX;
	for (k=p to r){
		if (L[i]<=R[j]) A[k] = L[i++];
		else A[k] = R[j++];
	}
}
```

-------------------------------------------------------

### 4.5 Quicksort
**Idea** (Divide and Conquer, 在Divide的時候sort花O(n))
1. Choose a **pivot** from the array
2. Partition: Reorder the array so that all elements with values *less* than the pivot come before the pivot, and all values *greater* than the pivot come after
3. Recursively apply the above steps to the sub-arrays

**Details**
* **Complexity:** T(n) = 2T(n/2) + O(n)
* **Data structure:** Array
* **Space:** `O(1)`
* **Best Case:** `O(nlog(n))`, sorted 每次pivot都剛好對半分，還是得把全部走過一次 Divide = O(n)
* **Worst Case:** All elements equal, `O(n^2)`, 每次都分成T(1)和T(n-1)，這樣樹高就會是n不是lgn
* **Average:** `O(nlog(n))`

**Advantages**
* Can be modified to use O(log(n)) space
* Very quick and efficient with large datasets
* Can be parallelized
* Divide and conquer algorithm

**Disadvantages**
* Not stable (could swap equal elements)
* Worst case is worse than Merge Sort

**Optimizations**
* Choice of pivot:
    * Choose median of the first, middle, and last elements as pivot
    * Counters worst-case complexity for already-sorted and reverse-sorted

**Visualization**
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Sorting/Animations/Quicksort.gif"/>
```c++
QuickSort(A, p, r){
	if (p<r) {
		q = Partition(A, p, r);
		QuickSort(A, p, q);
		QuickSort(A, q+1, r);
	}
}
Partition(A, p, r){
	x = A[p]; //pivot
	i = p-1;
	j = r+1;
	while(true){
		while (A[--j]<=x) break;
		while (A[++i]>=x) break;
		if(i<j){
			swap(A[i], A[j]);
		}else return j; //切分線發生在ji的中間，因此左邊那塊到j，右邊那塊從j+1開始
	}
}
```

-------------------------------------------------------

### 4.6 Non-Comparison-Based Sorter
- Counting sort
  - Assume n inputs in range [0...k]
  - time complexity = O(K+N)
  - space complexity = O(K+N)
  - not-inplace, stable
  - 總會會有三個Array，第一個是原本的A，第二個是新的排序好要丟進去的B，第三個是拿來計算counting的C
```c++
CountingSort(A, B, k){
	int C[k](); // 創counting矩陣
	for (int i = 0; i<A.length; i++) C[A[i]]++; // 填counting矩陣
	for (int i = 1; i<k; i++) C[i] = C[i] + C[i-1]; // 填counting矩陣
	for (int i = A.length-1; i>=0; i--){ //sorting
		B[ C[A[i]]-1 ] = A[i];
		C[A[i]]--;
	}
}
```
- Radix sort
  - Assume n inputs each with d-digits
  - time complexity = O(d(K+N))
  - space complexity = O(d(K+N))
```c++
RadixSort(A, d){
	for (d= 1 to d){ //對每一個digit做stable sort，從低位數sort到高
		Use a stable sorter to sort array A on digit i //最適合用counting sort，因為每個digit理當只有range1~9
	}
}
```
- Bucket sort
  - Distribute element to buckets (例如用第一個數字為區別，1開頭的放在一起，建起一個Adjacent List)
  - 然後把每個Bucket裡面的東西sort(理論上很少)
  - 把buckets merge起來

<img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Sorting/ClassicalSorter.png">

-------------------------------------------------------

### 4.7 Binary Search
**Idea:**
1. If current element, return
2. If less than current element, look left
3. If more than current element, look right
4. Repeat

**Data Structures:**
* Tree
* Sorted array

**Space:**
* `O(1)`

**Best Case:**
* `O(1)`

**Worst Case:**
* `O(log n)`

**Average:**
* `O(log n)`

**Visualization:**
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Searching/Animations/Binary%20Search.gif"/>
```c++
BinarySearch (A, start, end, key){
	if (start>end) return false;
	now = (start+end)/2
	if (A[now]==key) return now;
	else if (A[now]>key) return BinarySearch(A, start, now-1, key);
	else return BinarySearch(A, now+1, end, key);
}
```

-------------------------------------------------------

### 4.8 Depth-First Search (DFS)
**Idea:** 用遞迴去從根追到葉子
1. Start at root node
2. Recursively search all adjacent nodes and mark them as searched
3. Repeat

**Data Structures:**
* Tree
* Graph

**Space:**
* `O(V)`, `V = number of verticies`

**Performance:**
* `O(E)`, `E = number of edges`

**Visualization:**
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Searching/Animations/Depth-First%20Search.gif"/>
```c++
DFS(G){
	for (v in G.V){
		v.color = WHITE;
		v.prev = NULL;
	}
	time = 0;
	for (u in G.V){
		if (u.color==WHITE)
			DFS-Visit(G,u);
	}
}
DFS-Visit(G,u){
	time = time+1;
	u.d = time;
	u.color = GRAY;
	for (v in G.adj[u]){
		if (v.color == WHITE) {
			v.prev = u;
			DFS-VISIT(G,v);
		}
	}
	u.color = BLACK;
	time = time+1;
	u.f = time;
}
```

-------------------------------------------------------

### 4.9 Breadth-First Search (BFS)
**Idea:** 用queue去慢慢擴展出去
1. Start at root node
2. Search neighboring nodes first before moving on to next level

**Data Structures:**
* Tree
* Graph

**Space:**
* `O(V+E)`, `V = number of verticies`

**Performance:**
* `O(V+E)`, `E = number of edges`

**Visualization:**
* <img src="https://github.com/shannon112/cpp-cheat-sheet/blob/master/Searching/Animations/Breadth-First%20Search.gif"/>
```c++
// white undiscovered, gray discovered, black explored
BFS(G,s){
	for (v in G.V-s){
		v.color = WHITE;
		v.d = MAX;
		v.prev = NULL; //predecessor
	}
	s.color = GRAY; s.d = 0; s.prev = NULL;
	queue Q;
	Q.push_back(s);
	while(!Q.empty()){
		u = Q.pop_front();
		for (v in G.Adj[u]){
			if (v.color==WHITE){
				v.color = GRAY; v.d = u.d+1; v.prev = u;
				Q.push_back(v);
			}
		}
		u.color = BLACK;
	}
}
```

-------------------------------------------------------

### 4.10 Divide And Conquer
- independent subproblems
- divide the problem, solve the subproblems recursively, and then combine solutions to solve the original problem
- complexity: T(n)=theta(1), if n<=c ; T(n)=aT(n/b)+D(n)+C(n), otherwise. 可以畫recursion tree來解開T再加上D和C即可
- a: # of subproblems. n/b: size of subproblems. D(n): time to divide. C(n): time to combine.
- e.g. twoSum

-------------------------------------------------------

### 4.11 Dynamic Programming

- overlapping subproblems (need to check the solution is best or not)
- solve the subproblems recursively (time consuming) (top down)
- solve each subproblem just once iteratively (with memoization) (bottom up) 
- optimal substructure (剝洋蔥式的解法，所求必來自前一項，最終將追回base case)
- e.g. twoSum, horseRober

-------------------------------------------------------

### 4.12 Greedy Algorithm
- greedy-choice property (global optimal solution can be arrived at making a local optimal choice)
- optimal substructure (剝洋蔥式的解法，所求必來自前一項，最終將追回base case)
- e.g. fractional knapsack

-------------------------------------------------------

### 4.13 Complexity
- How to Compute O(log⁡N) Time Complexity
- <img width="624" alt="圖片" src="https://github.com/user-attachments/assets/2e3f9b6e-8fcc-42e2-9b11-e6b595277beb">
- <img width="650" alt="圖片" src="https://github.com/user-attachments/assets/2b91fd11-6b80-46ba-848c-c7446d2bfe69">
