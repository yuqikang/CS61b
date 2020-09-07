## Lesson 6. ALists, Resizing, vs. SLists
### Why Array Lists
Limitation of Linked list - slow to get item for long lists
Why would get be slow for long lists compared to getLast()? 
* Have to scan to desired position. Slow for any i not near the sentinel node. 
* using an array instead (no links). 

### The Naive AList
'''
public class AList {
	private int[] items;
	private int size; 

    /** Creates an empty list. */
    public AList() {
		items = new int[100];
		size = 0;
    }

    /** Resizes the underlying array to the target capacity. */
    private void resize(int capacity) {

    }

    /** Inserts X into the back of the list. */
    public void addLast(int x) {
		items[size] = x;
		size = size + 1;
    }

    /** Returns the item from the back of the list. */
    public int getLast() {
		return items[size - 1]; 
    }
    /** Gets the ith item in the list (0 is the front). */
    public int get(int i) {
		return items[i];
    }

    /** Returns the number of items in the list. */
    public int size() {
		return size; 
    }

    /** Deletes item from back of the list and
      * returns deleted item. */
    public int removeLast() {

    }
} 
'''
AList Invariants:
* The position of the next item to be inserted is always size.
* size is always the number of items in the AList.
* The last item in the list is always in position size -1. 

### The Allegory of the Cave
![](lmages/removelast.PNG)

### removeLast
'''
public int removeLast(){
	int x = getLast();
	size = size -1;
	return x;
}
'''

### Resizing Arrays
When the array gets too full, make a new array:
'''
private void resize(int capacity){
	int[] a = new int[capacity];
	System.arraycopy(items, 0, a, 0, size);
	items = a;
}

public void insertBack(int x){
	if (size = items.length){
		resize(size + 1);
	}
	items[size] = x;
	size += 1;
	}
'''

