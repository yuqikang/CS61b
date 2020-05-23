# CS61b
CS61b Data Structures, Spring 2019 UC Berkeley 

# Lecture 4. SSLists, Nested classes, Sentinel Nodes. 
### From IntList to SLList
Rewrite IntList to SLList
```
public class SLList {
	public IntNode first;

	public SLList(int x){
		first = new IntNode(x, null);
	}

	/* Adds x to the front of the list */
	public void addFirst(int x){
		first = new IntNode(x, first);
	}

	/* Returns the first item in the list. */
	public int getFirst(){
		return first.item;
	}

	public static void main(String[] args){
		/* Creates a list of one integer, namely 10*/
		SLList L = new SLList(10);
		L.addFirst(10);
		L.addFirst(5);
		System.out.println(L.getFirst());
	}
}
```
IntList vs. SLList
* SLList is easier to instantiate (no need to specify null)
* Simpler to use. Simply use the provided methods. 
