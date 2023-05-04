Download Link: https://assignmentchef.com/product/solved-csci235-project-3-zoorecord-is-a-bag-of-animals
<br>
Project3 will continue to build on Projects 1 and 2 to work with <strong>Inheritance, Templates, ADTs and file input.</strong> After completion of this project you must be very comfortable with compiling multiple classes as well as template classes (i.e. you do not compile them!!!) into one program, instantiating objects of a template class, basic inheritance and reading input from a file. <u>If you are not absolutely comfortable with all</u> <u>of this, please seek help immediately</u> (contact me or visit the lab to work with our UTAs).

In Project3 we will work with the ArrayBag class discussed during lecture. This project consists of <strong>two parts</strong>:

<ol>

 <li>Modify the ArrayBag class</li>

 <li>Implement a class ZooRecord which <u>inherits from </u><u>ArrayBag</u> and stores Animal objects (you will also make a small modification to the Animal class to support ZooRecord)</li>

</ol>

You will find the ArrayBag class (as discussed in lecture) on Blackboard under Course Materials / Project3.

<strong>First</strong> you <strong>must read the </strong><strong>ArrayBag interface</strong> and understand how it works. You will need to know how to use ArrayBag objects by understanding its interface.

<u>Note: </u>Reading interfaces is the way you learn to use language libraries, so this is great practice for that!

<strong>Implementation – 2 parts: </strong>

<strong>Work incrementally!</strong> Start from Part 1 (implement and test), when that runs correctly then move on to Part2.

<strong>Part1- ArrayBag modifications: </strong>

<ol>

 <li>Modify the add method so that it<u> will not allow duplicate items</u> to be added to the ArrayBag (conceptually the Bag becomes a Set).</li>

 <li>Implement <u>public</u> method display() to display the contents of the bag to standard output in the form “item1, item2, … , itemN
”</li>

</ol>




/**<strong>@post</strong> prints the contents of items_ to the standard output             separated by commas and followed by a new line.**/      <strong>void</strong><strong> display() </strong><strong>const</strong><strong>;</strong>

<ol start="3">

 <li>Overload <u>public</u> operator+= to implement Set Union (<strong>Hint: </strong>you can use other ArrayBag operations to implement this)</li>

</ol>




/** implements Set Union

The union of two sets A and B is the set of elements which are in A,      in B, or in both A and B.

<strong>@param</strong> a_bag to be combined with the contents of this (the calling) bag

<strong>@post</strong> adds as many items from a_bag as space allows

*/     <strong>void</strong> <strong>operator</strong><strong>+=(</strong><strong>const</strong><strong> ArrayBag&lt;T&gt;&amp; a_bag);</strong>

<strong>Note: </strong>Because ArrayBag is of <u>fixed size</u>, += will only copy as many items from a_bag as there is space available without deleting its original contents. <strong>Notice how fixed size can be an issue and force unintuitive implementations</strong>! We will address the fixed-size problem soon.

<ol start="4">

 <li>Overload <u>public</u> operator-= to implement Set Difference (<strong>Hint: </strong>you can use other ArrayBag operations to implement this)</li>

</ol>




/** implements Set Difference

The (set) difference between two sets A and B is the set that      consists of the elements of A which are not elements of  B      <strong>@param</strong> a_bag to be subtracted from this (the calling) bag

<strong>@post</strong> removes all data from items_ that is also found in a_bag

*/

<strong>void</strong> <strong>operator</strong><strong>-=(</strong><strong>const</strong><strong> ArrayBag&lt;T&gt;&amp; a_bag);</strong>




<ol start="5">

 <li>Overload <u>public</u> operator/= to implement Set Intersection (<strong>Hint: </strong>you can use other ArrayBag operations to implement this)</li>

</ol>




/** implements Set Intersection

The intersection of two sets A and B is the set that      consists of the elements that are in <strong>both</strong> A and B

<strong>@param</strong> a_bag to be intersected with this (the calling) bag

<strong>@post</strong> items_ no longer contains data not found in a_bag

*/     <strong>void</strong> <strong>operator </strong><strong>/=(</strong><strong>const</strong><strong> ArrayBag&lt;T&gt;&amp; a_bag); </strong>

Note that the overloaded operators are +<strong>= </strong>,  —<strong>=</strong> and /<strong>= </strong>(not +, — and /). Note also that these are all <strong>void </strong> functions. This means that these do not produce a new array that contains the union, difference and intersection respectively. Instead, they modify items_  to contain the union, difference and intersection respectively. Thus, in our set analogy, items_ corresponds to <u>both</u> set A and the resulting union/difference/ intersection, while a_bag corresponds to set B.

<strong>IMPORTANT: </strong>Please remember that you DO NOT compile (or include in your project) the implementation (.cpp) of a Template class. Please look at slide 38 from Lecture 3 and make sure you understand separate compilation with templates (it will probably help if, as suggested on slide 40, you first run a dummy test and make sure you can compile a simple/trivial template class)

<strong>Part2 –</strong> <strong>ZooRecord class:</strong><strong> </strong>

<strong> </strong>

Write a class, ZooRecord, that <strong>inherits from </strong><strong>ArrayBag </strong>and stores Animal objects. The ZooRecord class should have <u>at least</u> the following <u>public methods</u>:

<ol>

 <li>ZooRecord(); //default constructor for empty record</li>

 <li>/**parameterized constructor</li>

</ol>

<strong>@pre</strong> the input file is expected to be in CSV      (comma separated value) format as:

“animal_name,hair,feathers,eggs,milk,airborne,aquatic,predator,toothed, 
backbone,breathes,venomous,fins,legs,tail,domestic,catsize,class_type<strong>
</strong>”

<strong>@param</strong> input_file_name the name of  the input file

<strong>@post</strong> adds Animal objects to record as per the data in the input file

**/

ZooRecord(std::string input_file_name);

<ol start="3">

 <li>/**<strong>@post</strong> displays all animals in record, one per line by calling animal’s display method” **/ <strong>void</strong> display();</li>

</ol>

<u>You must also modify the <strong>Animal class </strong>as follows:</u><u> </u>

<ol start="4">

 <li>Add the display()method:</li>

</ol>

/**<strong>@post</strong> displays animal data in the form:

“animal_name is [not] domestic and [it is / is not] a predator<strong>
</strong>”

**/     <strong>void</strong> display();

<ol start="5">

 <li>Overload operator== for the Animal class, otherwise you will have a problem when the add() methods tries to compare two animals to add them to the ZooRecord. This operator can be a friend function, since it does not “belong” to either of the two Animals being compared,. <em><u>This statement is not trivial, if you don’t</u> <u>understand please ask for help from the UTAs in lab!</u></em></li>

</ol>




<strong>Testing: </strong>

<strong>Part1 – Testing your modification to ArrayBag: </strong>

Before you move to Part2, YOU MUST  make sure that your modifications to ArrayBag work correctly. To do so write your own main function (not for submission) that does the following:

<ul>

 <li>Instantiate two ArrayBag objects that stores integers</li>

 <li>Add integers to the two bags (some integers should be common to the two bags)</li>

 <li>Call += on one of the bags, display its contents and make sure the operation worked correctly (i.e. bag1∪bag2) and that your modification to add worked s.t. there are no duplicates. Also <strong>be sure your </strong><strong>dispaly()function displays the contents of the bag as specified </strong>in Part1 above (<u>Gradescope will rely on</u> <u>display() to check that other functions work correctly</u>)</li>

 <li>Call —= on one of the bags, display its contents and make sure the operation worked correctly (i.e. bag1 — bag2).</li>

 <li>Repopulate the bags s.t. some of their contents overlap, then call /= on one of the bags, display its contents and make sure the operation worked correctly
 (i.e. bag1 ∩ bag2).</li>

</ul>

<strong>Part2 – Testing the ZooRecord class: </strong>

Again in a main function (<u>not for submission</u>) do the following

<ul>

 <li>Instantiate a ZooRecord object with the name of an input file</li>

 <li>Display the record and make sure that all animals in the file were added to the ZooRecord. Again <strong>be sure your </strong><strong>display() function here has been overloaded to display Animals EXACTLY as specified above </strong>in Part2 above.</li>

</ul>

<strong>The Data: </strong>

The input file will be in <strong>csv</strong> (comma separated value) format, and each line corresponds to one Animal.

The data comes from the UCI Machine Learning repository (<a href="https://archive.ics.uci.edu/ml/datasets/zoo">https://</a>

<a href="https://archive.ics.uci.edu/ml/datasets/zoo">archive.ics.uci.edu/ml/datasets/zoo</a><a href="https://archive.ics.uci.edu/ml/datasets/zoo">)</a> , it consists of 101 animals from a zoo. There are 16 variables with various traits to describe the animals. The 7 Class Types are: Mammal (1), Bird (2), Reptile (3), Fish (4), Amphibian (5), Bug (6) and Invertebrate (7) This dataset is often used to predict the classification of the animals based upon the variables using machine learning techniques. In this course we will use it to illustrate the concept of Inheritance in OOP.

Each line in the input file has the following format:

animal_name,hair,feathers,eggs,milk,airborne,aquatic,predator,to othed,backbone,breathes,venomous,fins,legs,tail,domestic,catsize

,class_type

For this project you will only be concerned with those attributes found in the Animal class from Project 2, namely animal_name, predator and domestic. For each line read from the input file, the ZooRecord parameterized constructor will create an Animal object with these attributes and add it to the record.

You can find the input file named zoo.csv on Blackboard under Course Materials /

Project3

<strong>Review — reading the input (REVIEW ): </strong>

In C++ to read input from a file you need a file stream

#include &lt;fstream&gt;

Since we are only reading input you can use an ifstream object.

Since we are reading from a csv file, every animal is on a line. On each line, each data item is separated by a comma.

You may use string::getline() to read lines from the ifstream.

#include &lt;string&gt;

You may find it useful to use a stringstream to then read each piece of data (id, first_name and last_name) from each line you read from the input file.

#include &lt;sstream&gt;

You may use getline() to read data from the sstream as well. Remember that getline() may take a delimiter. The default delimiter is ‘
’, but if you are reading comma-separated values you can use ‘,’ as the delimiter. getline(stream, variable, delimiter); Don’t forget to:

<ul>

 <li>Open the stream before reading.</li>

 <li>Check that opening the stream did not fail before reading, and output (cout) an error message if it does fail.</li>

 <li>Close the stream after reading.</li>

</ul>

<strong>Note: Reading from input file should be familiar from CSci 135</strong>. If you need to review, lookup ifstream, sstream and string::getline()

References for each of these are easily found online: <a href="http://www.cplusplus.com/reference/fstream/ifstream/">http://www.cplusplus.com/reference/fstream/ifstream/</a><u> </u><a href="http://www.cplusplus.com/reference/sstream/stringstream/">http://www.cplusplus.com/reference/sstream/stringstream/</a><u> </u><a href="http://www.cplusplus.com/reference/string/string/getline/">http://www.cplusplus.com/reference/string/string/getline/</a>

If you need help with this even after having reviewed the documentation, please don’t hesitate to ask for help from the tutors in labB or make an appointment with me. After this project you will be expected to be able to read from csv files.