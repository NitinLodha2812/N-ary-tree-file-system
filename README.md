## N-ary Tree Data Backup

This project implements an efficient backup system using N-ary trees, leveraging the tree-like structure of directories in operating systems. The goal is to track and back up modified files by comparing hash trees, which represent the state of the file system. The key components of the project are:

N-ary Tree Construction: A N-ary tree (Merkle tree) is built from the file system, where each leaf node represents the hash of a file, and non-leaf nodes represent the hash of their children. This tree structure efficiently tracks changes in files by hashing data blocks. The implementation allows constructing the tree either from a file path or an existing hash tree stored in a text file. The tree is built using a parallelized DFS-like approach with OpenMP tasks to speed up the process.

Comparing N-ary Trees: By comparing the N-ary tree of the current file system with a previous backup, the system can quickly detect modified files. The comparison is done using a breadth-first search (BFS) algorithm, where matching nodes indicate no changes in the subtree, while differing hashes signal file modifications. This method efficiently identifies changes without needing to create a full copy of the file system.

Backup of Changes: Once modified files are detected, the system generates queries to back up only the changes. These queries handle file additions, modifications, and deletions. The backup system updates the existing backup rather than creating a new one, optimizing both space and time. Parallel processing further accelerates the execution of these backup operations.

The project demonstrates significant performance improvements when parallelizing the hash tree construction and backup process using OpenMP. For larger data sets, the parallel version of the program offers substantial speedup compared to the serial version, making it suitable for efficiently backing up large file systems.