# Aquatic C++ Coding Exercise

## Project

We need to track a large number of items for insertion via a key. We want the performance to be good, but we also want to minimize the performance variance so as to have a more stable performance metric to plan on. Currently, we use a traditional hash map for the task, and we’ve found that it is both too high on latency and has too high of a variance, when profiled. An internal developer has mentioned the concept of an Open Addressing Hash-Table, and we’d like to implement one so that we might compare its performance characteristics.

An open-addressing hash-table has an overly sized internal array, same as a traditional collision-list based hash-table, but instead of using the hash to find a collision list and then inserting the element in such a list, the item goes directly into the hashed location within the internal array. If an element is already there, we will place the new element in the first free location, by stepping incrementally from the hash location. As such, "collision lists" exist as consecutively filled elements in the internal array.

Your task is to create an open-addressing hash-table with at least the following:

* Default construction
* Insertion of elements via a key
* Retrieval of elements based on the key
* Reporting current size of the container

Notes:

* Repeated insertions for the same key should overwrite each other.
* The container should provide storage to some factor of what the machine will reasonably allow. (No predefined maximum number of items)
* We do not expect you to fully imeplement STL compatibility in this task, and would instead ask you to approach this problem in the manner in which you would expect to do so if given such a task.
* While templates are permissible, the intent of this exercise is to gauge your comfort in C++ programming while respecting your time. If template programming is not your forte, then feel free to just have the facility store ints, or strings, or whatever other basic type you feel appropriate, for now.
* At this time, we will leave removal of items as a future extension
* There is no explicit need for iterator support, though you are welcome to do so, if you feel it best for your implementation.


## Provided

Lacking any standard build environment, we provide a docker-based setup to get you going. The expectation is that the code provided would be able to build within this environment, but you are free to develop in whatever environment makes you comfortable.

The environment provides:

* centos 7
* gcc 10.1.0, built from source and installed in `/opt/gcc`
* gtest-devel installed via yum
* boost-devel installed via yum
* cmake3 (symbolycally linked as `/usr/bin/cmake` for convenience)
* removes default compilers to avoid confusion

To build docker image from source

`docker build . -t aquatic`

Run docker: (Take care to personalize to where you pulled this repo)

`docker run --rm -it -v /path/to/this/repo/on/your/system/:/workspace/ aquatic bash`

Inside Docker container:

```
cd /workspace/
mkdir debug && cd debug
cmake ..
make
```