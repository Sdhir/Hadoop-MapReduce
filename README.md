# Hadoop-MapReduce

Contains: Main.java, Map.java, Reduce.java 

----------
Main.java
----------
- Creates Job
- Runs the Map.class first and then Reduce.class
- Takes in Input and Output directory as arguments

-----------
Map.java
-----------
- Map class extends Mapper
- map function 
	- tracks the chapter number
	- removes puntuations
	- removes the stop words (Obtained stop words from stopwords.txt file)

Map output (for example):
Chapter 1 (where alice is repeated four times):
<alice,1>
<alice,1>
<alice,1>
<alice,1>
Chapter 2 (where alice is repeated once):
<alice,2>
Chapter 3 (where alice is repeated twice):
<alice,3>
<alice,3>

- This way, the number refers to the chapter.

-------------
Reduce.java
-------------
- Reduce class extends Reducer
- reduce function uses Hapmap counts how many times a word appears in each individual chapter.

Reduce output (for example):
<alice,1,1,1,1,2,3,3>

The output is further modified to store top K = 10 words which are common among all chapters
with more than W = 3 times repetetion of that word in a chapter.

Modified output (for example):
alice => Chapter Number 1    4
alice => Chapter Number 2    1
alice => Chapter Number 3    2
