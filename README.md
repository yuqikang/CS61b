# CS61b
CS61b Data Structures, Spring 2019 UC Berkeley 

# Lecture 4. SSLists, Nested classes, Sentinel Nodes. 
## From IntList to SLList
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


![](Images/Int_vs_SL.PNG)
* SLList is easier to instantiate (no need to specify null)
* Simpler to use. Simply use the provided methods. 
* SLList creates a middle between user and data structure. 
![](Images/vs2.PNG)


## Public vs. Private Nested Classes
Problems: Users of our class might be tempted to try to manipulate secret IntNode directly 


![](Images/private.PNG) 

Solution: <br/>
***a) Use the ```Private``` keyword to prevent code in other classes from using members of a class. <br/>***
Why Restrict Access?<br/>
* Less for user of class to understand
* Safe for you to change private methods. <br/>

***b) Use Nested class <br/>***
Why Nested Class?<br/>
* when a class doesn't stand on its own and is above subordinate to another class.
	
Statis Nested Classes: If the nested class never uses any instance variables or methods of the outer class, declare is static.
* Static classes can't access outer class's instance variables or methods.
* Results in a minor savings of memory.
   
![](Images/nested_class.PNG)
	
## Adding More SSList Functionality
***.addLast(int x)***
```public void addLast(int x):
	IntNode p = first;
	
	/* Move p until it reaches the end of the list */
	while (p.next != null) {
	     p = p.next
        }
	p.next = new IntNode(x, null);
```

***.Size()***
```
/** Returns the size of the list that starts at IntNode P. **/
private statis nt size(IntNode p){
    if (p.next == null){
    	return 1;
    }
    return 1 + size(p.next)
}
public int size(){
     return size(first);
}
```
