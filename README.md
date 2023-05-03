Download Link: https://assignmentchef.com/product/solved-cs2223-homework-3
<br>
<h1>Please copy these classes into your Homework area</h1>

<ul>

 <li>hw3.AVL à USERID.hw3.AVL</li>

 <li>hw3.BST à USERID.hw3.BST</li>

 <li>hw3.Heap à USERID.hw3.Heap</li>

 <li>hw3.TaleOfTwoCitiesExtractor à USERID.hw3.TaleOfTwoCitiesExtractor</li>

 <li>hw3.Question1 à USERID.hw3.Question1</li>

 <li>hw3.Question2 à USERID.hw3.Question2</li>

 <li>hw3.Question3 à USERID.hw3.Question3</li>

</ul>

You will refer to the existing InstrumentedSeparateChainingHashST class. Note you could also copy your hw2 TaleOfTwoCitiesExtractor which will work as is for HW3

<strong> </strong>

<h1>Q1. HeapSort Empirical Evaluation</h1>

Algorithm 2.7 in Sedgewick, Heapsort, shows how to use a heap to sort a comparable array. The code is provided for you in <strong>algs.hw3.Heap</strong>. The first step is to construct a heap from a Comparable[] array. This takes place in the constructHeap(a) method.

// construct heap from the raw array of which we know nothing. <strong>int</strong> n = a.length;

<strong>for</strong> (<strong>int</strong> k = n/2; k &gt;= 1; k–) { <em>  sink</em>(a, k, n);

}

If you look at this code with an eye towards its performance, it sure looks like the <strong>for</strong> loop will execute n/2 times (which means its performance is linearly dependent on the size of the array). You also know that the <strong>sink</strong> method behavior (in the worst case) is directly proportional to the log of the number of elements in the heap. Thus, at first glance, it looks like this behavior will be proportional to ~ (N*log N)/2.

It turns out that you can mathematically prove that the performance constructHeap is in direct proportion to N alone.  Your task is to instead count the number of comparisons and exchanges, and validate the proposition (page 323) that it will, in fact, require fewer than 2N compares and fewer than N exchanges to construct a heap from N items.

<strong>Copy </strong><strong>algs.hw3.Heap into </strong><strong>USERID.hw3</strong> and modify it to record empirical results. For the domain of data, use uniformly computed random numbers from 0 to 1 (such as you can generate from

StdRandom.uniform()), and generate a table of results (showing N, # of exchanges, and #comparisons) for N=16, 32, 64, … 512. For each size N, run T=100 trials, and record the maximum number of exchanges and comparisons you witnessed <strong>solely during the constructHeap</strong> <strong>construction</strong>.

Do your empirical results support the proposition? Explain why or why not.

Copy the Question1 class to USERID.hw3 and modify it so its output should look something like this:

N     MaxComp      MaxExch

16    21          11          NOTE YOUR NUMBERS WILL BE DIFFERENT THAN THESE

32    xxx         yyy

64    xxx  yyy 128 xxx  yyy

256 xxx            yyy

512 xxx            yyy




<h1>Q2. Empirical Evaluation of Symbol Table structures</h1>

This question explores the different structures that result from using binary search trees and separate chaining hash table to support the Symbol Table API, which allows you to associate a (key, value) pair for future retrieval.

Once again, using the <u>Tale Of Two Cities</u> data set, modify this program to produce the following table. This question is based on the number of comparisons needed to locate each key in the symbol table.

<ul>

 <li>For Binary Search Trees, the depth of a node reflects the distance from the root, and this depth is one value smaller than the total number of comparisons needed to locate that node in the tree</li>

 <li>The same is true of AVL trees</li>

 <li>For Separate Chaining Hash Symbol Tables, each of the buckets stores its size, and each of these will contribute to the overall values.</li>

</ul>

For example, If there were five (key, value) pairs stored in the symbol table implemented as above as follows (note that only the keys are shown).




In the above structures, the number of comparisons to find each of the five keys (note that hashing doesn’t count as a comparison) is:

<table width="178">

 <tbody>

  <tr>

   <td width="48"><strong>key </strong></td>

   <td width="44"><strong>BST </strong></td>

   <td width="45"><strong>AVL </strong></td>

   <td width="42"><strong>HT </strong></td>

  </tr>

  <tr>

   <td width="48">A</td>

   <td width="44">2</td>

   <td width="45">3</td>

   <td width="42">2</td>

  </tr>

  <tr>

   <td width="48">B</td>

   <td width="44">1</td>

   <td width="45">2</td>

   <td width="42">1</td>

  </tr>

  <tr>

   <td width="48">C</td>

   <td width="44">2</td>

   <td width="45">1</td>

   <td width="42">3</td>

  </tr>

  <tr>

   <td width="48">D</td>

   <td width="44">3</td>

   <td width="45">3</td>

   <td width="42">1</td>

  </tr>

  <tr>

   <td width="48">E</td>

   <td width="44">4</td>

   <td width="45">2</td>

   <td width="42">1</td>

  </tr>

  <tr>

   <td width="48">Avg.</td>

   <td width="44">2.4</td>

   <td width="45">2.2</td>

   <td width="42">1.6</td>

  </tr>

 </tbody>

</table>




Your task is to complete this experiment using the Tale Of Two Cities data set to record the count of each word in a symbol table. You will have to use put (key, value) properly. That is, for the first occurrence of a given word, w, you would put(w, 1). Use the existing API to determine when a word already exists in the symbol. For each subsequent occurrence of a given word, just increment the value associated with w by calling put() with a count that is one greater.

To be clear, the depth of a node in a binary search tree is the number of edges it takes to get to that node from the root. Thus the root of the binary search tree has a depth of zero. With regards to the number of comparisons which you need to output below, this is a reflection of how many comparisons it takes to determine whether a key value exists within the AVL, BST or Hash Symbol Table. The number of comparisons for a key value in the BST and AVL tree is 1 greater than the depth of the node. Why? Because you need to compare just to see if you have even found the key you are looking for, even when looking for the key associated with the root of a tree.

For the Hashtable, you don’t count the cost of hashing a key to its individual bucket. You only count the number of comparisons to find these keys. Note this part of the question is the trickiest part of this homework. Come to office hours if you have questions.

When you are done, your output should look like this:

There are 10650 unique words.

The Height of the BST is 29

The Height of the AVL is 15




N      1,   2,   3,   4,   5,   6,   7,   8,   9,  10,  11,  12,  13,  14,  15,  16,  17,  18,  19  …

#BST   1,   2,   4,   8,  15,  30,  57,  98, 159, 252, 383, 549, 740, 886, 997,1085,1053,1024, 955, …

#AVL   1,   2,   4,   8,  16,  32,  64, 128, 256, 512,1020,1944,2904,2583,1066, 110 #HT 2035,1977,1820,1549,1204, 867, 557, 331, 166,  92,  40,  11,   1




AVG. BST NumberOfComparisons:16.509671361502347

AVG. AVL NumberOfComparisons:12.716338028169014 AVG. HT NumberOfComparisons:3.6068544600938965 <strong>Tasks: </strong>

<ul>

 <li>Complete implementation of collect() in AVL</li>

 <li>Complete implementation of height() and height(Node) in BST</li>

 <li>Complete implementation of collect() in BST</li>

 <li>Complete implementation of Question2</li>

</ul>

Consider inserting the keys { “it”, “was”, “the”, “best”, “of”, “times”, “it”, “was”,”the”, “worst”, “of”, “times” } into a BST, an AVL and the Hast Table. The results appear on the next page. Note that the structures represent a symbol table, so the BST, AVL and Hash Table all associate the respective frequencies of each word in the structures (not shown below). The following words appear twice (“it”, “was”, “the”, “of”, “times”) and the words “best” and “worst” appear just once. So these keys would have either 2 or 1 associated with them.




<strong> </strong>

<table width="639">

 <tbody>

  <tr>

   <td width="212"><strong>BST TREE </strong></td>

   <td width="214"><strong>AVL TREE </strong></td>

   <td width="212"><strong>HASH TABLE (M=4) </strong></td>

  </tr>

  <tr>

   <td width="212"></td>

   <td width="214"><strong> </strong></td>

   <td width="212"><strong> </strong></td>

  </tr>

 </tbody>

</table>




With these structures, here are the counts of comparisons for locating each key.

<table width="261">

 <tbody>

  <tr>

   <td width="51"><strong>key </strong></td>

   <td width="70"><strong>BST </strong></td>

   <td width="70"><strong>AVL </strong></td>

   <td width="70"><strong>HT </strong></td>

  </tr>

  <tr>

   <td width="51">Best</td>

   <td width="70">2</td>

   <td width="70">3</td>

   <td width="70">1</td>

  </tr>

  <tr>

   <td width="51">It</td>

   <td width="70">1</td>

   <td width="70">2</td>

   <td width="70">3</td>

  </tr>

  <tr>

   <td width="51">Of</td>

   <td width="70">4</td>

   <td width="70">3</td>

   <td width="70">2</td>

  </tr>

  <tr>

   <td width="51">The</td>

   <td width="70">3</td>

   <td width="70">1</td>

   <td width="70">1</td>

  </tr>

  <tr>

   <td width="51">Times</td>

   <td width="70">4</td>

   <td width="70">3</td>

   <td width="70">1</td>

  </tr>

  <tr>

   <td width="51">Was</td>

   <td width="70">2</td>

   <td width="70">2</td>

   <td width="70">2</td>

  </tr>

  <tr>

   <td width="51">Worst</td>

   <td width="70">3</td>

   <td width="70">3</td>

   <td width="70">1</td>

  </tr>

  <tr>

   <td width="51">Avg.</td>

   <td width="70">2.714286</td>

   <td width="70">2.428571</td>

   <td width="70">1.571429</td>

  </tr>

 </tbody>

</table>




Output would look like this:

There are 7 unique words.

The Height of the BST is 3

The Height of the AVL is 2

N      1,   2,   3,   4,   5,   …

#BST   1,   2,   2,   2,

#AVL   1,   2,   4,

#HT    4,   2,   1,




AVG. BST NumberOfComparisons:2.7142857142857144

AVG. AVL NumberOfComparisons:2.4285714285714284

AVG. ST NumberOfComparisons:1.5714285714285714




As a further hint, please review the code example “CountingObject” I’ve made this available in day 18 and the “outputDepthInfo” method in BST as found in day 17. You will need to pull the latest version of the Algorithms D2020 repository to get this code.

<strong> </strong>

<strong> </strong>

<h1>Q3. Binary Search Trees</h1>

Using Binary Search Trees to build a Symbol Table that counts the number of occurrences of unique words in <em><u>The Tale Of Two Cities</u></em> by Charles Dickens. Copy the TaleOfTwoCitiesExtractor that you had used for HW2 into your USERID.hw3 package. Q2  Copy <strong>algs.hw3.Question3</strong> into your USERID.hw3 package and modify it for this problem.

<strong>Q3.1 (10 points) </strong>Complete the method that returns the Key whose Value is highest.

<strong>public</strong> String mostFrequent() { <strong>…</strong> }




You can add any number of helper methods as part of this assignment.

<strong>Q3.2 (15 points) </strong>Complete the method that prints in ascending order the number of words that appear only once in the Binary Search Tree (i.e., their count is 1) <strong>and returns the total number of keys sthat were printed. </strong>

<strong>public</strong> int printUnique() { <strong>…</strong> }




You can add any number of helper methods as part of this assignment. Note that the output will likely exceed your console history, so you will only see the last

<strong>Q3.3 (5 points)</strong> Question4 should construct a BST from the <em><u>Tale of Two Cities</u></em> and output the 10 most common words (together with their corresponding appearance counts). It does this by repeatedly deleting the key whose count frequency is highest in the BST until all values are printed. The output should look like:

Top ten most frequent words




<table width="85">

 <tbody>

  <tr>

   <td width="48">the</td>

   <td width="37">7983</td>

  </tr>

  <tr>

   <td width="48">and</td>

   <td width="37">4935</td>

  </tr>

  <tr>

   <td width="48">of</td>

   <td width="37">3999</td>

  </tr>

  <tr>

   <td width="48">to</td>

   <td width="37">3460</td>

  </tr>

  <tr>

   <td width="48">a</td>

   <td width="37">2908</td>

  </tr>

  <tr>

   <td width="48">in</td>

   <td width="37">2579</td>

  </tr>

  <tr>

   <td width="48">his</td>

   <td width="37">2005</td>

  </tr>

  <tr>

   <td width="48">it</td>

   <td width="37">2003</td>

  </tr>

  <tr>

   <td width="48">i</td>

   <td width="37">1913</td>

  </tr>

 </tbody>

</table>

that 1889

Number of words that appear once aa aaabusiness aamatter aback abandon … youths youties

youunder

5158 unique words.

<h1>Change Log</h1>

<ol>

 <li>ANY changes will appear here 2. Binary Search Tree has a height of 29.</li>

 <li>Clarified difference between Depth and #of Comparisons</li>

</ol>


