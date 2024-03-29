***Bioinformatics***
 
Project Authors:   
- Dominik Huffield
- Marcus Henke 

![banner](bioinfo.png)  

-----------------------------------
Layout of the B-Tree file on disk:
-----------------------------------

The layout of our btree binary disk file is as follows: Each Node on the disk consists of a Location; number of objects; isLeaf; Parent pointer; Child pointers; Tree Objects with the DNA long strand and the frequency of it occuring. 


|                   Node Layout on disk                      |
:------------------------------------------------------------:  
| -  Location size (int) 4 bytes                             |  
| -  Number of objects size (int), 4 bytes                   |  
| -  isLeaf boolean (int), four bytes                        |  
| -  parent Pointer size (int), four bytes                   |  
| -  Child pointer array, 4 bytes                            |  
| -  TreeObjects: DNA (long) & frequency (int) (8 & 4 bytes) |  
| -  DNA strand size (long), 8 bytes                         |  
| -  Frequncy size (int), 4 bytes                            |  
 


----------------------
Command Line Usage
----------------------
GeneBankCreateBTree.java   
>  java GeneBankCreateBTree <0/1(no/with Cache)> <degree> <gbk file> <sequence length> [<cache size>] [<debug level>]  
>   **debug level must be one or zero if used, and sequence length must be between 1 and 31.  
  
GeneBankSearch.java  
>  java GeneBankSearch <0/1(no/with Cache)> <btree file> <query file> [<cache size>] [<debug level>]  
>    **debug level must be one or zero if used.  

----------------------
Directions
----------------------

Run the GeneBankBTree class with any *.gbk file to create a BTree of DNA strands.  
The BTree will be stored in a binary data file in the format of [file].gbk.btree.data.k.t,  
where t is the degree of the BTree and k is the length of the DNA strands. Debug level 1 will  
write a dump file with all strand frequencies in the format of [file].gbk.btree.dump.t.  

The GeneBankSearch class will search through a given BTree file, searching for strands from a  
given query file and retrieving their frequencies. The retrieved data will be printed to a file  
in the format of [file]_query[k]_result. With debug level 0, the program will print the data  
to the console.   
