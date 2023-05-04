Download Link: https://assignmentchef.com/product/solved-csci340-assignment6-binary-tree-class
<br>
For this computer assignment, you are to write a C++ program to implement a class for binary trees. To deal with variety of data types, implement this class as a template<em>.</em>

The definition of the class for a binary tree (as a template) is given as follows:

<table width="0">

 <tbody>

  <tr>

   <td width="288">template &lt; class T &gt; class binTree { public:</td>

   <td width="30"> </td>

   <td width="193"> </td>

  </tr>

  <tr>

   <td width="288">      binTree ( );</td>

   <td width="30"> </td>

   <td width="193">  // default constructor</td>

  </tr>

  <tr>

   <td width="288">     unsigned height ( ) const;</td>

   <td width="30"> </td>

   <td width="193">  // returns height of tree</td>

  </tr>

  <tr>

   <td width="288">    virtual void insert ( const T&amp; );</td>

   <td width="30"> </td>

   <td width="193">  // inserts a node in tree</td>

  </tr>

  <tr>

   <td width="288">            void inorder ( void ( * ) ( const T&amp; ) ); protected:</td>

   <td width="30"> </td>

   <td width="193">  // inorder traversal of tree</td>

  </tr>

  <tr>

   <td width="288">            Node &lt; T &gt;* root; private:</td>

   <td width="30"> </td>

   <td width="193">   // root of tree</td>

  </tr>

  <tr>

   <td width="288">    unsigned height ( Node &lt; T &gt;* ) const;</td>

   <td width="30"> </td>

   <td width="193">   // private version of height ( )</td>

  </tr>

  <tr>

   <td colspan="3" width="512">  void insert ( Node &lt; T &gt;*&amp;, const T&amp; );                 // private version of insert ( )</td>

  </tr>

 </tbody>

</table>

void inorder ( Node &lt; T &gt;*, void ( * ) ( const T&amp; ) ); // private version of inorder ( ) };

Most of the <em>public</em> member functions of the binTree class call <em>private</em> member functions of the class (with the same name). These <em>private</em> member functions can be implemented as either <em>recursive</em> or <em>non-recursive,</em> but clearly, <em>recursive</em> versions of these functions are preferable because of their short and simple implementations in code. However, they require more memory and usually slower than their <em>non-recursive</em> versions in execution, especially for a large amount of input data.

Because of information hiding, a client is not permitted to access the binary tree directly, so the <em>root</em> of the tree is kept <em>protected</em> (not <em>private</em> because of future implementations of <em>derived </em>classes from the <em>base </em>class of the binTree), so it cannot be passed as an argument to any of the <em>public</em> functions of the tree. It is essential to have <em>private</em> utility functions, which act as interface between a client and the tree. The insert ( ) function of the binTree class is described as follows:

insert ( const T&amp; x ) : This <em>virtual</em> function can be used to insert a node with the data value x in a binary tree, applying the following technique: if the tree is empty, then the new node will be the <em>root</em> of the tree with the value x; otherwise, the left or the right subtree is randomly selected and the value x is inserted in that side. To implement the random selection, you can use the following RNG.

typedef enum { left_side, right_side } SIDE;

SIDE rnd ( ) { return rand ( ) % 2 ? right_side : left_side; }

Put the implementation of your binTree class in the following header file:




1

<ul>

 <li>binTree.h: Definition of the class Node, which represents the nodes in a binary tree, can be found in the header file Node.h. To use the class Node in your program, include the header file Node.h by inserting the statement: #include “/home/cs340/progs/17f/p6/Node.h” at the top of your header file.</li>

</ul>




The source file prog6.cc contains the driver program. In addition to the main ( ) routine, it has the implementations of the following routines (as templates) and the definitions of the two RNGs used in the main ( ) routine.




o template &lt; class T &gt; void print ( const T&amp; x ): o template &lt; class T &gt; void print_vals (  binTree &lt; T &gt;&amp; tree, const string&amp; name );

The unary function print ( ) can be used as an argument to the member functions inorder ( ) to print the value of its argument x. The function print_vals ( ) does the followings: first, it prints name, which is the name of the tree, and it also prints the height of the tree. Then, it calls the member function inorder ( ) to print the data values in the tree in inorder. The class RND1 can be used to generate random integers in the range [ LOW1 = –999, HIGH1 = 999 ] and the class RND2 can be used to generate random floating-point numbers in the range [ LOW2 = –999.99, HIGH2 = 999.99 ]. The function objects RND1 ( ) and RND2 ( ), generated from these classes, are used to fill in the random values in vector containers vector &lt; int &gt; A ( N1 ) and vector &lt; float &gt; B ( N2 ) by using the generate ( ) function in STL, where N1 = 100 and N2 = 50 are the corresponding sizes of these two vectors. The main ( ) routine copies the random values from vectors A and B and inserts them in the binary trees first and second, respectively. At the end, the data values in the binary trees first and second are printed out on stdout with LSIZE = 12 numbers in a single line.




The source file of the driver program prog6.cc, in directory: ~cs340/progs/17f/p6, is provided. To compile and link the driver program with the system library routines, execute: Make N=6. To test your binary-tree class, execute: Make execute N=6. This command executes the driver program and displays the output as well as any error messages both on the terminal screen and in prog6.out. After you are done with the program, you don’t need its object and executable files any more. To delete them, execute: Make clean.




The correct output of this program can be found in file prog6.out, which is in the same directory with prog6.cc. If the program fails to generate the correct output, then to debug the program, copy the file prog6.cc in your own directory, uncomment some of the statements in that file, recompile and link the modified program, and then execute again.




When your program is ready, submit the header file of your binary-tree class to your TA, executing: mail_prog.340 binTree.h.





