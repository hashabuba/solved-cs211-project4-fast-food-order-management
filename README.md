Download Link: https://assignmentchef.com/product/solved-cs211-project4-fast-food-order-management
<br>
<h1></h1>

For this project, write a C program that will implement a food ordering system used in a fast food restaurant. This restaurant only serves burgers and salads and when people want to order food, they give their name and food choices to the cashier and then wait until those in front of them have been served.  The program must use <strong>a linked list</strong> to implement the queue-like data structure.

The linked list is to maintain the following information for each group that is waiting:

<ul>

 <li>name (we assume a maximum name length of 30 characters)</li>

 <li>food items (number of burgers and salads ordered)</li>

 <li>in-restaurant status: whether the group has called ahead or is waiting in the restaurant</li>

</ul>




The system allows you to call and put your order in before you arrive at the restaurant, but it does not take orders for a specific time and date (i.e. 4 burgers and 2 salads for 7pm on Saturday).  Note: these call-ahead groups will still need to check in when they arrive, so the cashier knows they are waiting in the restaurant.




Groups are added to the order list when they call-ahead or when they arrive at the restaurant.  Groups are always added to the end of the order list.  The system will require that each name used be unique.  So when a group is added to the order list, the system must make sure that no other group is already using that name.




The restaurant staff working in the kitchen have a steady speed in preparing food and they work on one order at a time. On average, preparing a salad takes 5 minutes while burger takes 10 minutes.

The system needs to track how many food items have been ordered and provide customers with an estimated wait time.




You can assume that every time an order is being called, it will go to the first group in line. However, in order to pick up the food, the group needs to be present at the restaurant. If they are not, then the system will call the next eligible group for pick up (an eligible group is a group that the number of burgers and salads they ordered is less than or equal to prepared order).







The commands used by this system are listed below and are to come from standard input.  Your program is to prompt the user for input and display error messages for unknown commands or improperly formatted commands.   Note that the name of the group when given will be given as the last item on the input line.  The name of the group may contain white space characters in the middle of the name but not at the beginning or end of the name.  Each command given must display some information about the command being performed.  Code to implement this interface is provided in the program <strong>proj4base.c</strong>.
















<table width="623">

 <tbody>

  <tr>

   <td width="150">Command</td>

   <td width="473">Description</td>

  </tr>

  <tr>

   <td width="150"><strong>q </strong></td>

   <td width="473">Quit the program.</td>

  </tr>

  <tr>

   <td width="150"><strong>? </strong></td>

   <td width="473">List the commands used by this program and a brief description of how to use each one.</td>

  </tr>

  <tr>

   <td width="150"><strong>a &lt;#burgers&gt; &lt;#salads&gt; &lt;name&gt;  </strong></td>

   <td width="473">Add the order to the order list using the given order and name specifying the group is waiting in the restaurant.  The order’sinformation is added to the end of the list.  If the name already exists in the order list, give an error message and do not add the information.</td>

  </tr>

  <tr>

   <td width="150"><strong>c &lt;#burgers&gt; &lt;#salads&gt; &lt;name&gt; </strong></td>

   <td width="473">Add the order to the order list using the given order and name specifying the order as a call ahead order.  The order’s information is added to the end of the list.  If the name already exists in the order list, give an error message and do not add the information.</td>

  </tr>

  <tr>

   <td width="150"><strong>w &lt;name&gt; </strong></td>

   <td width="473">Mark the call ahead order using the given name as waiting in the restaurant.  If the name does not exist is the order list or is not a call ahead group, give an error message.</td>

  </tr>

  <tr>

   <td width="150"><strong>r &lt;#burgers&gt; &lt;#salads&gt; </strong></td>

   <td width="473">Retrieve and remove the first order on the order list that is waiting in the restaurant and contains less than or equal to number of prepared burgers and salads.  Note that “first” is the order that has been in the order list the longest.</td>

  </tr>

  <tr>

   <td width="150"><strong>l &lt;name&gt; </strong></td>

   <td width="473">List total number of orders that are in the order list in front of the order specified by the given name. If the name does not exist, give an error message.</td>

  </tr>

  <tr>

   <td width="150"><strong>t &lt;name&gt; </strong></td>

   <td width="473">Give an estimated waiting time based on the order list knowing preparing burgers will take 10 minutes and preparing salads takes 5.If the name does not exist, give an error message.</td>

  </tr>

  <tr>

   <td width="150"><strong>d </strong></td>

   <td width="473">Display the total number of orders in the order list.  Also display the names, order details and in-restaurant status of all orders in the order list in order from first to last.</td>

  </tr>

 </tbody>

</table>




Note that <strong>&lt;#burgers&gt;</strong> and <strong>&lt;#salads&gt;</strong> are to be integer values and <strong>&lt;name&gt;</strong> is a list of characters.  The &lt; and &gt; symbols are NOT part of the input but being used to describe the input.

<h1>Use of C struct and C functions</h1>

When writing your code, you MUST create a C struct for the nodes in the linked list of the order list.  These data items must include the following (and may include others if desired):

<ul>

 <li>the name of the order</li>

 <li>the integer variables specifying details of the order (number of burgers and salads)</li>

 <li>the in-restaurant status (you should use an enum!)</li>

 <li>a pointer to the next node in the list</li>

</ul>




The pointer for the head of the linked list MUST be declared as a local variable in main() or some other function.  <strong>It may NOT be global. </strong> If you wish to have the head of the list enclosed in a structure with some other information, that is OK (but certainly not required).  The variable used to access this structure; however, may not be global.  Each operation performed on the linked list MUST be done in its own function.  These functions must take the head of the linked list as the FIRST parameter.










<h1>Linked List Operations/Functions</h1>

You must write C functions for the following 8 operations.  These functions must be called when the specified commands are given as input.

<strong>addToList ( )</strong> – This operation is to add a new node to the end of the linked list.  This is to be used when the <strong>a</strong> and <strong>c</strong> commands are given as input.

<strong>doesNameExist ( )</strong> – This operation is to return a Boolean value indicating whether a name already exists in the linked list.  This is to be used when the <strong>a, c, w, t</strong> and <strong>l</strong> commands are given as input.

<strong>updateStatus ( )</strong> – This operation is to change the in-restaurant status when a call-ahead order arrives at the restaurant.  This operation will return a FALSE value if that order is already marked as being in the restaurant.  This is to be used when the <strong>w</strong> command is given as input.

<strong>retrieveAndRemove ( )</strong> – This operation is to find the first in-restaurant order that matches the order prepared for pick up at the counter.  This operation is to return the name of group.  This group is to be removed from the linked list.  This is to be used when the <strong>r</strong> command is given as input.

<strong>countOrdersAhead ( )</strong> – This operation is to return the number of orders waiting ahead of an order with a specific name.  This is to be used when the <strong>l</strong> command is given as input.

<strong>displayWaitingTime( ) </strong>– This operation is to return the estimated waiting time for the specific name. The function will check the number of burgers and salads ordered ahead of the specified name and using known preparing time (10 minutes for burger and 5 minutes for salad) calculates the estimated wait time. This is to be used when <strong>t </strong>command is given as input.

<strong>displayOrdersAhead ( )</strong> – This operation traverses down the list until a specific order name is encountered.  As each node is traversed, print out that node’s orders.  This command is to be used when the <strong>l</strong> command is given.

<strong>displayListInformation ( )</strong> – This operation to traverse down the entire list from beginning to end.  As each node is traversed, print out that node’s name, order details and in-restaurant status.  This command is to be used when the <strong>d</strong> command is given as input.

Note that there may be a many-to-many relationship between the commands in the user interface and the required functions.  For example, the l command (“list”) relies on the following functions: doesNameExist(), countOrdersAhead() and displayOrdersAhead().

<h1>Command Line Argument: Debug Mode</h1>

Your program is to be able to take one optional command line argument, the -d flag. When this flag is given, your program is to run in “debug” mode. When in this mode, your program is to display each order’s information as you traverse through the linked list of the order list.  Note that for the w, r, t and l commands, the entire list may not be traversed, so you only display the part of the list that is needed to be traversed to complete the command.

When the flag is not given, this debugging information should not be displayed. One simple way to set up a “debugging” mode is to use a boolean variable which is set to true when debugging mode is turned on but false otherwise. This variable may be a global variable.  Then using a simple if statement controls whether information should be output or not.

if ( debugMode == TRUE )  printf (” Debugging Information 
”);

<h1>Provided Code for the User Inteface</h1>

The code given in proj4base.c <strong>should</strong> properly provide for the user interface for this program including all command error checking.  This program has no code for the linked list. It is your job to write the functions for the specified operations and make the appropriate calls.  Most of the changes to the existing proj4base.c program need to be made in each of the <strong>doXXXX ( )</strong> functions.  Look for the comments of:




// add code to perform this operation here




Note: the head of the linked list is required to be a local variable in main and you are required to pass the head of the linked to the operation functions.  All of the <strong>doXXXX ( )</strong> functions currently have no parameters.  It will then be expected that you will modify the function signatures of the doXXXX() functions to allow for this information to be passed as required.




<h1>MULTIPLE SOURCE CODE FILES</h1>

Your program is to be written using at least three source code files.  It must also have a makefile and a header file to help with the compilation of the program.  All of the storage structure code (the linked list code) is to be in one source code file.  The code in proj4base.c is to be separated into two different source code files.

The following functions from proj4base.c are to be in one source code file (these are the user interface functions):

<ul>

 <li>main()</li>

 <li>clearToEoln()</li>

 <li>getNextNWSChar()</li>

 <li>getPosInt()</li>

 <li>getName()</li>

 <li>printCommands()</li>

</ul>

The following functions from proj4base.c are to be in another source code file (these are the functions that interact with the linked list functions):

<ul>

 <li>doAdd()</li>

 <li>doCallAhead()</li>

 <li>doWaiting()</li>

 <li>doRetrieve()</li>

 <li>doList()</li>

 <li>doDisplay()</li>

 <li>doEstimateTime()</li>

</ul>

The third source code file is to have the code that you are writing that will perform the linked list implementation:  The functions in this source code file will include the following functions plus any other you write to handle the linked list:

<ul>

 <li>addToList()</li>

 <li>doesNameExist()</li>

 <li>updateStatus()</li>

 <li>retrieveAndRemove()</li>

 <li>countOrdersAhead()</li>

 <li>displayOrdersAhead()</li>

 <li>displayListInformation()</li>

 <li>displayWaitingTime()</li>

</ul>




If you add additional functions to your program, you can add those to whichever source code file seems appropriate for that function (or create a fourth source code file or even a fifth).

You must also create a header file.  The job of the header file is to contain the information so the source code files can talk to each other.  The header file (.h file) should contain the function prototypes and any struct and/or typedef statements.  Please review the .h file in the example below.




The makefile MUST separately compile each source code file into a “.o” file and separately link the “.o” files together into an executable file.   Review the makefile in the example below to see how this is done.  The command to create the .o file is:

gcc –c program1.c

The command to link the files program1.o, program2.o and program3.o into an executable file is:

gcc program1.o program2.o program3.o

The above command will just name the executable file using the default name of a.out, most often the –o option is given to provide a specific name for the executable file.    gcc program1.o program2.o program3.o –o program.exe




<strong>Example of Multiple Source Code Files  </strong>

Consider the program contained in the following files:

<ul>

 <li><u>c</u></li>

 <li><u>c</u></li>

 <li><u>h</u></li>

 <li><u>makefile</u></li>

</ul>

This example shows how to set up this simplest of multiple source code file program. Note that max1.c and max2.c just contain functions and a #include of max.h. The file max.h contains the prototypes (or forward declarations) for all of the functions that are called from outside its source code file and any “globally” needed information.




The makefile is a special file that helps in the compilation of the source code into the object files into the executable file. A makefile is executed by the use of the <strong>make</strong> command. The syntax of a makefile can be strange. The makefile will contain multiple rules.  Each rule has the following syntax:




target:  dependencyList

commandLine







The multiple rules in the make file are separated by a blank line.  Also note<strong> (this is VERY </strong>

<strong>IMPORTANT) </strong>the commandLine must use a TAB for its indentation!  An example of a rule is:




max1.o: max1.c max.h          gcc -c max1.c




The <strong>commandLine</strong> is <strong>gcc -c max1.c</strong>, which will compile the source code file of max1.c into the object code file of max1.o.




The <strong>target</strong> in the above example is the file <strong>max1.o</strong>, which is also the name of the file created when the commandLine is executed.  This relationship is what causes makefiles to work.




The <strong>dependencyList</strong> in the above example is the two files: <strong>max1.c</strong> and <strong>max.h</strong>, which are the files needed for the commandLine to properly run.  Again, this relationship is what causes makefiles to work.




The make command uses the timestamps of the files in the target and the dependencyList.  If any file in the dependencyList has a more recent timestamp than the target file, the commandLine is executed.  The idea is that if the user has recently changed either <strong>max1.c</strong> or <strong>max.h</strong>, then the object file <strong>max1.o</strong> needs to be re-compiled.  Make is designed to help the programmer keep track of what needs to be compiled next.




Make and makefile tutorials can be found at:

<ul>

 <li><u>http://mrbook.org/tutorials/make/</u></li>

 <li><u>http://www.gnu.org/software/make/manual/make.html</u></li>

 <li><u>http://www.opussoftware.com/tutorial/TutMakefile.htm</u></li>

</ul>




<h1><em>Coding Style </em></h1>

Don’t forget to use good coding style when writing your program.  Good coding style makes your program easier to be read by other people as the compiler ignores these parts/differences in your code.  Elements of good code style include (but may not be limited to):

<ul>

 <li>Meaningful variable names</li>

 <li>Use of functions/methods</li>

 <li>Proper indentation</li>

 <li>Use of blank lines between code sections</li>

 <li>In-line comments</li>

 <li>Function/method header comments</li>

 <li>File header comments</li>

</ul>

The Code Review Checklist also hints at other elements of good coding style.

<strong><em> </em></strong>

<strong><em> </em></strong>