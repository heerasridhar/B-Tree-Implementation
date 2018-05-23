# B-Tree-Implementation

Methods that need to be implemented in BTreeFile.java are:

1.insert

2._insert 

3.NaiveDelete  

- Insert() method

  The Insert part was implemented by considering two cases. First the header page is checked to be INVALID_PAGE, if true then the tree is empty and a new page is created. The first new page created is called the LEAF page. If the header page is NOT an INVALID_PAGE calling the _INSERT function inserted the key and Record Id.  The ROOTPAGE and HEADERPAGE is pinned and unpinned accordingly. After creating a RootEntry it is evaluated to NULL to check if a leaf split propagated to the root and performed a root split. The entryPage contains the data of the new entry which was given up from the level down in the recurrence process. The old root split becomes the left child of the new root.

- _Insert() method

  First check if the type of the page is INDEX or LEAF. For index recurse and try to split and for leaf insert key and record Id. Then check if the child is split if so, move it to the index page. If there is no space in the INDEX page again perform split to insert a key. For making an equal split create a temporary entry and copy all the key values to it and if there is no space in leaf, split and copy it to the index level the first record of the right child. In equal split Compare the key using BT.keyCompare ,If the value is positive the key goes on the newLeafPage Else on the currentLeafPage. After transferring the records current page to new page , insert and delete records from current page. Unpin the page when the page is dirty.

- NaiveDelete method

  For implementing _NaiveDelete create a leaf page and an iterator ,using the function Findrunstart and determine the first page and     recordId of the keys. If the record id is found delete the keys and Unpin the page as it is dirty.
