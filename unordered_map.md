# map and unordered_map
unordered_map是存储容器，该容器存储由键值和映射值组合而成的元素，并允许基于键对单个元素进行快速检索。 
unordered_map下的函数

## Capacity: empty ans size
**empty()**: Returns a bool value indicating whether the unordered_map container is empty

**size()**: Return container size 

``` C++
// unordered_map::empty
#include <iostream>
#include <unordered_map>

int main ()
{
  std::unordered_map<int,int> first;
  std::unordered_map<int,int> second = {{1,10},{2,20},{3,30}};
  std::cout << "first " << (first.empty() ? "is empty" : "is not empty" ) << std::endl;
  std::cout << "second " << (second.empty() ? "is empty" : "is not empty" ) << std::endl;
  std::cout << "second.size() is " << second.size() << std::endl;
  return 0;
}
```

## Iterators

**begin()**: Return iterator to beginning 

Returns an iterator pointing to the first element in the unordered_map container (1) or in one of its buckets (2).

unordered_map无法保证每次访问的第一个元素相同，但是从begin到end一定能遍历到所有元素
> Notice that an unordered_map object makes no guarantees on which specific element is considered its first element. But, in any case, the range that goes from its begin to its end covers all the elements in the container (or the bucket), until invalidated.

``` C++
// unordered_map::begin/end example
#include <iostream>
#include <unordered_map>

int main ()
{
  std::unordered_map<std::string,std::string> mymap;
  mymap = {{"Australia","Canberra"},{"U.S.","Washington"},{"France","Paris"}};

  std::cout << "mymap contains:";
  for ( auto it = mymap.begin(); it != mymap.end(); ++it )
    std::cout << " " << it->first << ":" << it->second;
  std::cout << std::endl;

  std::cout << "mymap's buckets contain:\n";
  for ( unsigned i = 0; i < mymap.bucket_count(); ++i) {
    std::cout << "bucket #" << i << " contains:";
    for ( auto local_it = mymap.begin(i); local_it!= mymap.end(i); ++local_it )
      std::cout << " " << local_it->first << ":" << local_it->second;
    std::cout << std::endl;
  }

  return 0;
}
```

end()
cbegin()
cend()
at()
find()
count()
equal_range()
emplace()
insert()
erase()
clear()
swap()
bucket_count()
max_bucket_count()
bucket_size()
bucket()
load_factor
Return load factor (public member function)
max_load_factor
Get or set maximum load factor (public member function )
rehash
Set number of buckets (public member function )
reserve
Request a capacity change (public member function)

Observers
hash_function
Get hash function (public member type)
key_eq
Get key equivalence predicate (public member type)
get_allocator
