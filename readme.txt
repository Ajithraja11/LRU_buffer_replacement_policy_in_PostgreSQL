Least Recently Used(LRU)
 
     "LRU can be implemented in the buffer manager using a linkedlist of pointers to frames with
      pin_count O. A frame is added to the end of the linkedlist when it becomes a
      candidate for replacement (that is, when the pincount goes to 0). The page
      chosen for replacement is the one in the frame at the head of the linkedlist"

MY UNDERSTANDING AND IMPLEMENTATION OF THE PROEJECT :-
 - In clock algorithm, usage count is used where in the LRU it is not required. In the LRU only refcount is used.
 So I removed usage count in the files mentioned (freelist.c,bufmgr.c).

 - In the file freelist.c, the following functions are modified
	~StrategyGetBuffer(), when ever this function is called the very first buffer in the free_list will be returned.
	~StrategyFreeBuffer(), This function receives a buffer as a parameter, the buffer will be added to the tail of the free list.
 - In the file bufmgr.c, the following functions are refered
 	~unpinBuffer(), This function unpins the buffer and if the pincount reaches zero then that buffer will be added back to free list

TESTING:
 - For testing the implementation of the LRU the codes elog(LOG, "Add buf %d\n", buf->buf_id); and elog(LOG, "Get buf %d\n", buf->buf_id);
 have been added into StrategyFreeBuffer and StrategyGetBuffer. So that whenever a buffer is removed or added to list buffer name will be printed.  

 







