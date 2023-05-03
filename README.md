Download Link: https://assignmentchef.com/product/solved-cs-202-computer-science-ii-project-8
<br>



<strong> </strong>







<strong>Objectives:  </strong>The main objectives of this project are to test your ability to create and use list-based dynamic data structures. A review of your knowledge to manipulate dynamic memory, classes, pointers and iostream to all extents, is also included. You may from now on freely use <strong>square bracket</strong>-indexing, <strong>pointers</strong>, <strong>references</strong>, all <strong>operators</strong>, the <strong>&lt;cstring&gt;</strong> library, and the <strong>std::string</strong> type as you deem proper.




<strong>Description: </strong>

For this project you will create List classes. There will have to be two separate List-based implementations, one Array-based, and the other Node-based.




<strong>Array-based List: </strong>

The following header file extract is used to explain the required specifications for the class (the actual header ArrayList.h file is provided and accompanies the Project description):




<strong>… </strong>

<table width="629">

 <tbody>

  <tr>

   <td width="576"><strong>class</strong> <strong>ArrayList</strong><strong>{ </strong></td>

   <td width="53"></td>

  </tr>

  <tr>

   <td width="576"><strong>  </strong><strong>friend</strong> <strong>std::ostream&amp;</strong> <strong>operator&lt;&lt;</strong><strong>(</strong><strong>std::ostream&amp;</strong><strong> os,          </strong><strong>                                </strong><strong>const ArrayList&amp;</strong><strong> arrayList);   </strong><strong>public:</strong></td>

   <td width="53"><strong>//(i) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>ArrayList</strong><strong>();                                          </strong></td>

   <td width="53"><strong>//(1) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    ArrayList</strong><strong>(</strong><strong>size_t </strong><strong>count, </strong><strong>const DataType&amp;</strong><strong> value);          </strong></td>

   <td width="53"><strong>//(2)</strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>ArrayList</strong><strong>(</strong><strong>const ArrayList&amp;</strong><strong> other);                      </strong></td>

   <td width="53"><strong>//(3)</strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>~ArrayList</strong><strong>();                                         </strong><strong> </strong></td>

   <td width="53"><strong>//(4)</strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>ArrayList&amp; </strong><strong>operator=</strong><strong> (</strong><strong>const ArrayList&amp;</strong><strong> rhs);            </strong><strong> </strong><strong> </strong></td>

   <td width="53"><strong>//(5) </strong></td>

  </tr>

  <tr>

   <td colspan="2" width="629"><strong>    </strong><strong>DataType*</strong> <strong>First</strong><strong>();                                          </strong><strong>//(6) </strong><strong>    </strong><strong>DataType*</strong> <strong>Last</strong><strong>();                                            </strong><strong>//(7)</strong><strong>      </strong><strong>    </strong><strong>DataType*</strong> <strong>Find</strong><strong>(</strong><strong>const DataType &amp;</strong><strong> target,                       </strong><strong>//(8) </strong></td>

  </tr>

 </tbody>

</table>

<strong>                   </strong><strong>DataType * &amp;</strong><strong> previous,         </strong><strong>const DataType *</strong><strong> start = </strong><strong>NULL</strong><strong>);  </strong>

<strong>      </strong>

<strong>    </strong><strong>DataType*</strong> <strong>InsertAfter</strong><strong>(</strong><strong>const DataType&amp;</strong><strong> target,                </strong><strong>//(9)</strong><strong>                           </strong><strong>const DataType&amp;</strong><strong> value);     </strong>

<strong>    </strong><strong>DataType*</strong> <strong>InsertBefore</strong><strong>(</strong><strong>const DataType&amp;</strong><strong> target,              </strong><strong>//(10) </strong><strong>                           </strong><strong>const DataType&amp;</strong><strong> value); </strong>

<table width="633">

 <tbody>

  <tr>

   <td width="432"><strong>    </strong><strong>DataType*</strong> <strong>Erase</strong><strong>(</strong><strong>const DataType&amp;</strong><strong> target); </strong><strong> </strong><strong>      </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="153"><strong>         </strong><strong>//(11) </strong></td>

  </tr>

  <tr>

   <td width="432"><strong>    </strong><strong>DataType&amp;</strong> <strong>operator[]</strong><strong> (</strong><strong>size_t</strong><strong> position);  </strong><strong>     </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="153"><strong>        </strong><strong>//(12)</strong></td>

  </tr>

  <tr>

   <td width="432"><strong>    </strong><strong>size_t</strong> <strong>size</strong><strong>() </strong><strong>const</strong><strong>;                    </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="153"><strong>        </strong><strong>//(13) </strong></td>

  </tr>

  <tr>

   <td width="432"><strong>    </strong><strong>bool</strong> <strong>empty</strong><strong>() </strong><strong>const</strong><strong>;                    </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="153"><strong>      </strong><strong>//(14) </strong></td>

  </tr>

  <tr>

   <td width="432"><strong>    </strong><strong>void</strong> <strong>clear</strong><strong>();                          </strong></td>

   <td width="48"><strong> </strong></td>

   <td width="153"><strong>        </strong><strong>//(15)</strong><strong>  </strong></td>

  </tr>

 </tbody>

</table>

<strong> </strong><strong>  private: </strong>

<strong>    </strong><strong>void</strong> <strong>resize</strong><strong>(</strong><strong>size_t</strong><strong> count);                                </strong><strong>//(16)</strong>

<strong>                         </strong>

<strong>    </strong><strong>DataType * </strong><strong>m_array;     </strong><strong>size_t</strong><strong> m_size;     </strong><strong>size_t </strong><strong>m_maxsize; </strong>

<strong>}; … </strong>




The <strong>ArrayList </strong>Class will contain the following<strong> private </strong>data members:

<ul>

 <li><strong>m_array,</strong> a DataType class type Pointer, <u>pointing</u> to the <u>Dynamically Allocated Array</u> It is the container for the ArrayList data, and will have to be resized (reallocated) whenever it needs to grow to accommodate more data than it can fit, and possibly whenever it should trim down when it takes up too much space.</li>

 <li><strong>m_size</strong>, a size_t, keeps track of how many DataType elements are currently stored &amp; considered valid inside m_array. <em>Note</em>: this has to be properly <u>initialized</u> and <u>updated </u>each time the dynamically allocated memory is changed.</li>

 <li><strong>m_maxsize</strong>, a size_t, denoting how many DataType type objects can fit in total in the currently allocated memory of the m_array. <em>Note</em>: this has to be properly <u>initialized</u> and <u>updated </u>each time the dynamically allocated memory is changed, and that generally m_size ≤ m_maxsize.</li>

</ul>

, will have the following <strong>private</strong> helper methods<strong>: </strong>

<strong>(16) resize </strong>– will deallocate the dynamic memory pointed to by m_array and then allocate enough total memory to fit the size_t count number of elements. Also, the original m_array data should be carried (copied) over to the newly allocated one.

<em>Note A</em>: When enlarging the m_array container, only the valid ArrayList elements (m_size in total) should be copied over, and the rest (m_maxsize-m_size in total) should have the DataType Default ctor value.

<em>Note B</em>: When shrinking down the m_array container, in case the new m_maxsize cannot fit all the m_size elements of the ArrayList, then the last ones are just discarded. If it can, then it copies over only the valid ArrayList elements (m_size in total), and the rest (m_maxsizem_size n total) should have the DataType Default ctor value.

, and will have the following<strong> public </strong>member functions:

<ul>

 <li><strong>(1) Default Constructor</strong> – will instantiate a new list object with no valid data. <em>Note</em>: What needs to be initialized in this case?</li>

 <li><strong>(2) Parametrized Constructor </strong>– will instantiate a new list object, which will hold size_t count number of elements in total, all of them initialized to have the same value as the DataType value parameter. <em>Note</em>: Has to properly handle allocation.</li>

 <li><strong>(3) Copy Constructor</strong> – will instantiate a new ArrayList object which will be a separate copy of the data of the other ArrayList object which is getting copied. <em>Note</em>: Remember Deep and Shallow object copies.</li>

 <li><strong>(4) Destructor </strong>– will destroy the instance of the ArrayList object. <em>Note</em>: Any allocated memory pointed-to by m_array has to be deallocated in here.</li>

 <li><strong>(5) operator= </strong>will assign a new value to the calling ArrayList object, which will be an exact copy of the rhs ArrayList object. Returns a reference to the calling object to be used for cascading operator= as per standard practice. <em>Note</em>: Think what needs to happen before allocating new memory for the new data to be held by the calling object.</li>

 <li><strong>(6) First </strong>returns a pointer to the first (valid) element of m_array, or NULL if it fails. <em>Note</em>: A reason for failing can be that the list is empty.</li>

 <li><strong>(7) Last </strong>returns a pointer to the last (valid) element of m_array, or NULL if it fails. <em>Note</em>: A reason for failing can be that the list is empty.</li>

 <li><strong>(8) Find </strong>returns a pointer to the first (valid) element of m_array, which is found to have the same value as the passed parameter DataType target (the equality operator== as overloaded in class DataType should be used to check that). If it fails (it does not find the value it searched for), it returns NULL. Also, it takes in By-Reference a DataType Pointer parameter, and sets it to the Address of the target’s predecessor element. If the search fails, or if the target element is found to be the first and has no predecessor, previous should be set to NULL.</li>

</ul>

<strong>(Extra Functionality (not required for 100pt grade): </strong>The method also takes in a DataType Pointer named start, which indicates where it should start searching in the list. If this is passed as NULL, it denotes to start searching from the first element. Otherwise, this can be used to start a recursive search in case an element exists twice (otherwise Find will always return the first element’s address).

<ul>

 <li><strong>(9) InsertAfter </strong>first finds the DataType element target, and then inserts after it in the list a new element of the value DataType value. Returns DataType Pointer to the element it just inserted (or NULL if it failed). <em>Note</em>: Try to think through what you are doing, and sketch out how it’s going to work. Think of all possible cases, e.g. inserting in the middle, at the end, in the start, what happens if m_array already has a size that fits the element, or if it should be resized to fit the new element, etc.</li>

 <li><strong>(10) InsertBefore </strong>first finds the DataType element target, and then inserts before it in the list a new element of the value DataType value. Returns DataType Pointer to the element it inserted (or NULL if it failed). <em>Note</em>: Try to think through what you are doing, and sketch out how it’s going to work. Think of all possible cases, e.g. inserting in the middle, at the end, in the start, what happens if m_array already has a size that fits the element, or if it should be resized to fit the new element, etc.</li>

 <li><strong>(11) Erase </strong>first finds the DataType element target, and then removes it from the list. Returns a DataType Pointer to the element right after the one it just removed (if the last it removed was the last in the list, it should return NULL). <em>Note</em>: Try to think through what you are doing, and sketch out how it’s going to work. Think of all possible cases, e.g. removing in the middle, the first element, the last element.</li>

 <li><strong>(12) operator[] </strong>will allow by-reference accessing of a specific DataType object at index int position within the allocated m_array. <em>Note</em>: Should not care if the position requested is more than the m_array size.</li>

 <li><strong>(15) size </strong>will return the size of the current list. <em>Note</em>: This is the m_size of m_array and not its m_maxsize, i.e. it is the number of valid DataType entries inside it.</li>

 <li><strong>(16) empty </strong>will return a bool, true if the list is empty, and false otherwise.</li>

 <li><strong>(17) clear </strong>will clear the contents of the list, so after its call it will be an empty list object. <em>Note</em>: Does this need to perform memory deallocation?</li>

</ul>

as well as a friend function:

<ul>

 <li><strong>(i) operator&lt;&lt; </strong>will output (to terminal or file depending on the type of ostream&amp; os object passed as a parameter to it) the content of the calling ArrayList object. <em>Note</em>: it will do so by traversing the list and calling the insertion operator&lt;&lt; on the valid DataType elements contained within it.</li>

</ul>




<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong>Node-based List: </strong>

The following header file extract is used to explain the required specifications for the class (the actual header NodeList.h file is provided and accompanies the Project description):




<strong>… </strong>

<table width="629">

 <tbody>

  <tr>

   <td width="576"><strong>class</strong> <strong>NodeList</strong><strong>{ </strong></td>

   <td width="53"></td>

  </tr>

  <tr>

   <td width="576"><strong>  </strong><strong>friend</strong> <strong>std::ostream&amp;</strong> <strong>operator&lt;&lt;</strong><strong>(</strong><strong>std::ostream&amp;</strong><strong> os,                                     </strong><strong>const NodeList&amp;</strong><strong> nodeList); </strong><strong>  public: </strong></td>

   <td width="53"><strong>//(i) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>NodeList</strong><strong>();                                           </strong></td>

   <td width="53"><strong>//(1)</strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>NodeList</strong><strong>(</strong><strong>size_t</strong><strong> count, </strong><strong>const DataType&amp; </strong><strong>value);          </strong></td>

   <td width="53"><strong>//(2) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>NodeList</strong><strong>(</strong><strong>const NodeList&amp;</strong><strong> other);                        </strong></td>

   <td width="53"><strong>//(3)</strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>~NodeList</strong><strong>();                                           </strong><strong> </strong></td>

   <td width="53"><strong>//(4)</strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>NodeList&amp;</strong> <strong>operator=</strong><strong> (</strong><strong>const NodeList&amp;</strong><strong> rhs);              </strong><strong> </strong></td>

   <td width="53"><strong>//(5)</strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>Node*</strong> <strong>First</strong><strong>();                                         </strong></td>

   <td width="53"><strong>//(6) </strong></td>

  </tr>

  <tr>

   <td width="576"><strong>    </strong><strong>Node*</strong> <strong>Last</strong><strong>();                                         </strong><strong>      </strong></td>

   <td width="53"><strong>//(7)</strong></td>

  </tr>

  <tr>

   <td colspan="2" width="629"><strong>    </strong><strong>Node*</strong> <strong>Find</strong><strong>(</strong><strong>const DataType &amp;</strong><strong> target,                           </strong><strong>//(8) </strong></td>

  </tr>

 </tbody>

</table>

<strong>               </strong><strong>Node * &amp;</strong><strong> previous, </strong>

<strong>    </strong><strong>const Node *</strong><strong> start = </strong><strong>NULL</strong><strong>);  </strong>

<strong>      </strong>

<strong>    </strong><strong>Node*</strong> <strong>InsertAfter</strong><strong>(</strong><strong>const DataType&amp;</strong><strong> target,                    </strong><strong>//(9)</strong><strong>                       </strong><strong>const DataType&amp;</strong><strong> value);         </strong>

<strong>    </strong><strong>Node*</strong> <strong>InsertBefore</strong><strong>(</strong><strong>const DataType&amp;</strong><strong> target,                  </strong><strong>//(10) </strong><strong>                       </strong><strong>const DataType&amp;</strong><strong> value); </strong>

<strong>    </strong><strong>Node*</strong> <strong>Erase</strong><strong>(</strong><strong>const DataType&amp;</strong><strong> target);                  </strong><strong>//(11) </strong>

<strong> </strong>

<strong>      </strong>

<strong>    </strong><strong>DataType&amp;</strong> <strong>operator[]</strong><strong> (</strong><strong>size_t</strong><strong> position);                   </strong><strong>//(12a) </strong><strong>    </strong><strong>const </strong><strong>DataType&amp;</strong> <strong>operator[]</strong><strong> (</strong><strong>size_t</strong><strong> position) </strong><strong>const</strong><strong>;       </strong><strong>//(12b)</strong>

<strong>     </strong>

<strong>    </strong><strong>size_t</strong> <strong>size</strong><strong>() </strong><strong>const</strong><strong>;          </strong><strong>//(13) </strong><strong>    </strong><strong>bool</strong> <strong>empty</strong><strong>() </strong><strong>const</strong><strong>;            </strong><strong>//(14) </strong><strong>    </strong><strong>void</strong> <strong>clear</strong><strong>();           </strong><strong>//(15)</strong><strong>  </strong>

<strong> </strong><strong>  private: </strong>

<strong>    </strong><strong>Node * </strong><strong>m_head; </strong>

<strong>}; … </strong>




The <strong>NodeList </strong>Class will contain the following<strong> private </strong>data members:

<ul>

 <li><strong>m_head,</strong> a Node class type Pointer, <u>pointing</u> to the <u>Dynamically Allocated Node</u> object considered as the first element of the list. <em>Note</em>: If the list is empty m_head should be NULL.</li>

</ul>

,and will have the following<strong> public </strong>member functions:

<ul>

 <li><strong>(1) Default Constructor</strong> – will instantiate a new list object with no data (no Nodes). <em>Note</em>: What needs to be initialized in this case?</li>

 <li><strong>(2) Parametrized Constructor </strong>– will instantiate a new list object, which will hold size_t count number of elements (Nodes) in total, all of them initialized to hold the same value as the DataType value parameter. <em>Note</em>: Has to properly handle allocation.</li>

 <li><strong>(3) Copy Constructor</strong> – will instantiate a new list object which will be a separate copy of the data of the other NodeList object which is getting copied. <em>Note</em>: Remember Deep and Shallow object copies.</li>

 <li><strong>(4) Destructor </strong>– will destroy the instance of the NodeList object. <em>Note</em>: Any allocated memory taken up by elements (Nodes) belonging to the list has to be deallocated in here.</li>

 <li><strong>(5) operator= </strong>will assign a new value to the calling NodeList object, which will be an exact copy of the rhs NodeList object. Returns a reference to the calling object to be used for cascading operator= as per standard practice. <em>Note</em>: Think what needs to happen before allocating new memory for the new data to be held by the calling object.</li>

 <li><strong>(6) First </strong>returns a pointer to the first element (Node) of the list, or NULL if the list is empty.</li>

 <li><strong>(7) Last </strong>returns a Pointer to the last element (Node) of the list, or NULL if the list is</li>

 <li><strong>(8) Find </strong>returns a pointer to the first element (Node) of the list, that holds the same value as passed parameter DataType target (the equality operator== as overloaded in class DataType should be used to check that). If it fails (it does not find the value it searched for inside a Node), it returns NULL. Also, it takes in By-Reference a Node Pointer parameter named previous, and sets it to the Address of the target Node’s predecessor element (also a Node). If the search fails, or if the target element is found within the first Node of the list and has no predecessor, previous should be set to NULL.</li>

</ul>

<strong>(Extra Functionality (not required for 100pt grade): </strong>The method also takes in a Node Pointer named start, which indicates where it should start searching in the list. If this is passed as NULL, it denotes to start searching from the first element (Node). Otherwise, this can be used to start a recursive search in case an element exists twice (otherwise Find will always return the first element’s address).

<ul>

 <li><strong>(9) InsertAfter </strong>first finds the element (a Node) that contains DataType target, and then inserts after it a new element (a Node) that holds the value DataType value. Returns a Node Pointer to the element (a Node) it inserted (or NULL if it failed). <em>Note</em>: Try to think through what you are doing, and sketch out how it’s going to work. Think of all possible cases, e.g. inserting in the middle, at the end, in the start, etc.</li>

 <li><strong>(10) InsertBefore </strong>first finds the element (a Node) that contains DataType target, and then inserts before it a new element (a Node) that holds the value DataType value. Returns a Node Pointer to the element (a Node) it inserted (or NULL if it failed). <em>Note</em>: Try to think through what you are doing, and sketch out how it’s going to work. Think of all possible cases, e.g. inserting in the middle, at the end, in the start, etc.</li>

 <li><strong>(11) Erase </strong>first finds the element (a Node) that contains DataType target, and then removes it from the list. Returns a Node Pointer to the element (a Node) right after the one it just removed (if the last it removed was the last Node in the list, it should return NULL). <em>Note</em>: Try to think through what you are doing, and sketch out how it’s going to work. Think of all possible cases, e.g. removing in the middle, the first element, the last element.</li>

 <li><strong>(12a,12b) operator[] </strong>(const and non-const qualified) will allow by-Reference accessing of a specific DataType object within a Node at an index size_t position within the list. <em>Note</em>: Since this is not an Array-based implementation, the size_t position index is a “fake index”, just an incremental value such that position=0 corresponds to the first element (a Node) in the list and each subsequent element corresponds to ++position.</li>

 <li><strong>(15) size </strong>will return the size of the current list. <em>Note</em>: Since this is not an Array-based implementation, the function has to traverse the list to find how many elements (Nodes) are contained within it.</li>

 <li><strong>(16) empty </strong>will return a bool, true if the list is empty, and false otherwise.</li>

 <li><strong>(17) clear </strong>will clear the contents of the list, so after its call it will be an empty list object. <em>Note</em>: Does this need to perform memory deallocation?</li>

</ul>







as well as a friend function:

<ul>

 <li><strong>(i) operator&lt;&lt; </strong>will output (to terminal or file depending on the type of ostream&amp; os object passed as a parameter to it) the content of the calling NodeList object. <em>Note</em>: it will do so by traversing the list and calling the insertion operator&lt;&lt; on the valid DataType elements contained within the list’s elements (Nodes).</li>

</ul>




The DataType.h and DataType.cpp files are provided fully implemented. Also, the ArrayList.h and NodeList.h header files are provided, and NodeList.h provides a class Node implementation in it as well. You will create the necessary ArrayList.cpp and NodeList.cpp source files to implement the range of required functionalities You should also create a source file proj6.cpp which will be a test driver for your classes.

<strong>Do not forget to initialize pointers and/or set them to NULL appropriately where needed. Do not forget to perform allocation, dellocation, dellocation-&amp;-reallocation of dynamic memory when needed! Memory accesssing without proper allocation will cause Segmentation Faults. Forgetting to deallocate memory will cause Memory Leaks! </strong>




<strong>The completed project should have the following properties: </strong> Ø Written, compiled and tested using Linux.

<ul>

 <li>It must compile successfully on the department machines using Makefile(s), which will be invoking the g++ compiler. Instructions how to remotely connect to department machines are included in the Projects folder in WebCampus.</li>

 <li>The code must be commented and indented properly.</li>

</ul>

Header comments are required on all files and recommended for the rest of the program. Descriptions of functions commented properly.

<ul>

 <li>A one page (minimum) typed sheet documenting your code. This should include the overall purpose of the program, your design, problems (if any), and any changes you would make given more time.</li>

</ul>

<strong> </strong>

<strong>Turn in:</strong> Compressed Header &amp; Source files, Makefile(s), and project documentation.




<strong>Submission Instructions: </strong>

<ul>

 <li>You will submit your work via WebCampus</li>

 <li>Name your code file proj8.cpp</li>

 <li>If you have header file, name it proj8.h</li>

 <li>If you have class header and source files, name them as the respective class (ArrayList.h ArrayList.cpp NodeList.h NodeList.cpp) This source code structure is not mandatory, but advised.</li>

 <li>Compress your:

  <ol>

   <li>Source code</li>

   <li>Makefile(s)</li>

   <li>Documentation Do not include executable  Ø Name the compressed folder:</li>

  </ol></li>

</ul>

PA#_Lastname_Firstname.zip

Ex: PA8_Smith_John.zip























