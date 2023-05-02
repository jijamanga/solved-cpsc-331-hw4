Download Link: https://assignmentchef.com/product/solved-cpsc-331-hw4
<br>



This assignment consists of two parts. The first part consists of problems that will give you more practice working with hash tables and sorting algorithms. The second part consists of a coding exercise that asks you to implement a shortest path algorithm for a graph. You will also get some practice working with multiple source files and Java applets.

<h1>Part I</h1>

<ol>

 <li>Hash tables (5 points)

  <ul>

   <li>Consider an open-address hash table with uniform hashing. Give upper bounds on the expected number of probes in an unsuccessful search and on the expected number of probes in a successful search when the load factor is 3/4 and when it is 7/8. Consider all three schemes discussed in class namely: linear probing, quadratic probing, and double hashing. Tabulate your results for comparison.</li>

   <li>Suppose that in the separate chaining scheme, we also keep the lists in sorted order. With this modification, what is the running time for successful searches, unsuccessful searches, insertions, and deletions? State your answers in terms of the load factor <em>α</em>.</li>

  </ul></li>

 <li>(5 points)</li>

</ol>

This question deals with the heapsort algorithm shown below.

<strong>function </strong>Heapsort(<em>arr</em>) Heapify array arr;

<strong>for </strong><em>i </em>= <em>n </em>− 1 <em>down to </em>1 <strong>do </strong>swap arr[<em>i</em>] with arr[0]; restore heap property for the tree arr[0]<em>,…,</em>arr[<em>i </em>− 1] by percolating down the root;

<h2>end end</h2>

<ul>

 <li>Identify a suitable loop invariant that will help you show the correctness of heapsort.</li>

 <li>Show that your loop invariant holds by showing the initialization and maintenance steps.</li>

</ul>

You can assume that the <em>percolate down </em>operation is correct.

<ul>

 <li>Use your loop invariant to show the partial correctness of heapsort.</li>

</ul>

<ol start="3">

 <li>(7 points)</li>

</ol>

This question deals with the quick sort algorithm.

(a) Suppose that we modify the partitioning algorithm so that it always partitions an input array of length <em>n </em>into two partitions in such a way that the length of the left partition is <em>n </em>− <em>K </em>and the length of the right partition is <em>K </em>− 1 (for some <strong>constant </strong><em>K</em>, where <em>K &gt; </em>0). Let us refer to this partitioning algorithm as KPartition.

Now consider the following variation of quick sort called <strong>KQuickSort</strong>:

<strong>function </strong>KQuickSort(int[] A, int low, int high) <em>n </em>= high – low + 1; <strong>if </strong><em>n &lt; K </em><strong>then</strong>

insertionSort(A, low, high) ; <strong>else</strong>

q = KPartition(A, low, high) ; KQuickSort (A, low, q-1) ;

KQuickSort (A, q+1, high) ; <strong>end</strong>

<h2>end</h2>

Let <em>T</em>(<em>n</em>) denote the worst-case number of steps to run KQuickSort on input arrays of size <em>n</em>. Complete the following recurrence relation for <em>T</em>(<em>n</em>). Assume that KPartition takes Θ(<em>n</em>) steps to partition an array of size <em>n</em>.

( <em>n &lt; K,</em>

<em>T</em>(<em>n</em>) ≤

<em>n </em>≥ <em>K.</em>

<ul>

 <li>Use the substitution method to find an upper bound on <em>T</em>(<em>n</em>). For simplicity, assume that <em>n </em>is a multiple of <em>K</em>, i.e. <em>n </em>= <em>m </em> <em>K </em>(where <em>m </em>is a non-negative integer).</li>

 <li>Using the Big-O notation, give an asymptotic expression for the worst-case running time of KQuickSort. A proof is not required.</li>

 <li>How does the worst-case asymptotic running time of KQuickSort compare with that of quick sort?</li>

</ul>

<ol start="4">

 <li>(3 points)</li>

</ol>

Prove that a tree with <em>n </em>vertices has <em>n </em>− 1 edges.

<h1>Part II</h1>

In this coding exercise, you will implement a shortest path algorithm that finds the shortest path between two nodes (if any) in a maze. You can <em>either </em>use a breadth first search (BFS) to find the shortest unweighted path, <em>or </em>(for an added bonus) use Dijkstra’s shortest path algorithm to determine both weighted and unweighted shortest paths.

<h2>Introduction</h2>

You are given a maze that is represented as a graph consisting of an <em>n </em>× <em>n </em>grid of vertices. Vertices in the maze are connected via <em>weighted </em>undirected edges to form paths as shown in the figure below.

The vertices are numbered from 1 to <em>n</em><sup>2 </sup>in a column-major fashion as shown above. The connectivity in the graph is represented in a text file. The first line of this text file consists of the number <em>n </em>and the rest of the lines consist of three integer entries per line in the format:

&lt;fromVertex&gt; &lt;toVertex&gt; &lt;weight&gt;

In other words, each line after the first corresponds to an edge in the graph and there are as many entries as the number of edges. The edges are bidirectional, i.e. each edge appears twice in the file.

For the example graph pictured above, please see the file maze.txt. The first few lines from this file are:

4

1 2 11

<ul>

 <li>5 11</li>

 <li>1 11</li>

 <li>3 8</li>

 <li>2 8</li>

</ul>

3 4 8

<ul>

 <li>7 8</li>

 <li>3 8</li>

 <li>1 11</li>

</ul>

…

<h2>Shortest Unweighted Path</h2>

<em>For this part, you can ignore the edge weights.</em>

Your task is to determine the shortest path from a source vertex to a target vertex using a breadth first traversal. Source and target vertex pairs will be specified via an input query file that consists of one pair per line. For each pair, please determine the shortest path from the source to the target and use the the supplied MazeVisualizer to visualize the result. If there is no path between a given pair, please indicate that by printing out an appropriate message.

Each line in the input query file has the following format:

&lt;source vertex&gt; &lt;target vertex&gt;

For example, for the source and target vertices 1 and 12 in the figure above, the input line is:

1 12

and the result is pictured below.

Please write a Java program that performs the following tasks:

<ul>

 <li>Reads the maze information from an input file and uses an appropriate data structure to store this information.</li>

 <li>Reads source and target vertex pairs from an input query file. For each pair, perform a BFS to find the shortest path (ignoring edge weights) from the source to the target. Adjacent vertices should be enqueued in ascending order of vertex number. <em>Alternatively, if you are implementing the bonus portion (see below), your program should implement this using Dijkstra’s algorithm with unit edge weights.</em></li>

 <li>Visualizes the paths using the supplied MazeVisualizer. MazeVisualizer is a Java applet that provides methods to add edges and paths to be visualized. Multiple paths can be visualized simultaneously. The main method in MazeVisualizer includes relevant calls that demonstrate its use.</li>

</ul>

Your program will be invoked from the command line as follows: java HW4 maze-file query-file

Please use the supplied maze file and the figure above to test your program. Additional test files and associated output will be made available closer to the due date. Your program should be able to infer the number of vertices in the maze from the maze file. Please do not hard code this information as you will be required to test with larger mazes.

<em>Unlike previous assignments, if you need to make use of auxiliary data structures, please feel free to make use of Java collection classes. The implementation of the shortest path algorithm must be your own. The use of any other code that is not your own is not allowed.</em>

<h2>Bonus: Shortest Path using Dijkstra’s Algorithm</h2>

Optionally, please implement Dijkstra’s shortest path algorithm to find the shortest <em>weighted </em>path between the source and target vertices supplied in the query file. Visualize these paths using the supplied MazeVisualizer. Your program will be invoked from the command line as follows:

java HW4 [option] maze-file query-file

The command-line argument [option] can take one of two values:

–unweighted: determine the shortest unweighted path. –weighted: determine the shortest weighted path.

To help you test your program, the shortest path using Dijkstra’s algorithm for the pair 1 and 12 (for the example above) is pictured below.

Additional test files and output will be supplied closer to the due date.

<em>If you need to make use of auxiliary data structures, please feel free to make use of Java collection classes. The implementation of Dijkstra’s shortest path algorithm must be your own. The use of any other code that is not your own is not allowed.</em>


