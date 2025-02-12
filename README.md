
# WordCount-Using-MapReduce-Hadoop

This repository is designed to test MapReduce jobs using a simple word count dataset.

Project Overview

Developing a Word Count program using Hadoop MapReduce. Counting words in a text file and printing them in descending order according to their frequency of occurrence. The program is written in Java using Maven for project management. It's basically in Hadoop's MapReduce framework for distributed processing.

Approach and Implementation
Mapper Logic:
The Mapper will process each line in the input dataset, split the text into words, and emit key-value pairs, where the key is a word and the value is 1.
For example:
Input: Hello Hadoop
Mapper Output: (Hello, 1), (Hadoop, 1)
Reducer Logic:
The Reducer gets those key-value pairs grouped from the Mapper, sums the counts of each word, and emits each word's final count.
For example:
Input to Reducer: (Hadoop, [1, 1, 1])
Reducer Output: (Hadoop, 3)
Sorting by Frequency:
Since by default Hadoop provides the output results in alphabetical order, there will be one additional step of user-defined sort applied after the reduce phase for printing the output with the words' frequency in descending order.
Execution Steps

Build the Project:

Build Java Program with Maven and Package into .jar files.

Prepare Input File:

Prepare a text file with the required dataset.

Upload to HDFS:

Then upload the input file to HDFS by creating the input directory.

Run the MapReduce Job:

Use the .jar file to run the Hadoop job with properly specified Input and Output directories in HDFS.

Get Output:

After job completion, retrieve the output file from the output directory in HDFS.

Sort Results by Frequency:

Post-process the output file such that results are sorted in order of frequency in descending order.
Challenges Faced & Solutions

Class Missing during Execution Error:

Initially, it was quite troublesome since the Word Count could not be found in the class during execution. This was removed because of the package declaration in the .java file, followed by a change in ".class" when exporting in the source code matched the project’s directory structure.

Sorting by Frequency:

Hadoop does not natively sort the results by frequency. A custom script was added in the post-processing step to sort the results correctly.
Sample Input and Output
Sample Input
kotlin
CopyEdit
Hello world
Hello Hadoop
Hadoop is powerful
Hadoop is used for big data

Expected Output
kotlin
CopyEdit
Hadoop 3
Hello 2
is 2
used 1
for 1
big 1
data 1
powerful 1
world 1