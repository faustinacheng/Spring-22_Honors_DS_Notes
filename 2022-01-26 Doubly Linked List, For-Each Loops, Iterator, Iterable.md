26 Jan 2022

## Doubly Linked List with Sentinel Nodes (Cont.)

Code:

```java
public class MyLinkedList<AnyType> implements List<AnyType> {

    private int theSize; // how many values in list (begin/end markers don't count)
    private int modCount = 0;
    private Node<AnyType> beginMarker;
    private Node<AnyType> endMarker;
 
    /**
     * This is the doubly-linked list node.
     */
    private static class Node<AnyType> {
        // Nested class is a class inside another class
        // If they're declared static, they behave almost like top-level classes and can't see the superclass' variables
        // If they're not static, they can access the superclass' variables
        
        public AnyType data;
        public Node   prev;
        public Node   next;

        public Node( AnyType d, Node<AnyType> p, Node<AnyType> n ) {
            data = d; prev = p; next = n;
        }
        
    }

    /**
     * Construct an empty LinkedList.
     */
    public MyLinkedList( ) {
        clear( );
     }

     /**
     * Change the size of this collection to zero.
     */
    public void clear( ) {
        beginMarker = new Node( null, null, null );
        endMarker = new Node( null, beginMarker, null );
        beginMarker.next = endMarker;
        
        theSize = 0;
        modCount++;
    }
    
    /**
     * Returns the number of items in this collection.
     * @return the number of items in this collection.
     */
    public int size( ) {
        return theSize;
    }
    
    public boolean isEmpty( ) {
        return size( ) == 0;
    }
    
    /**
     * Adds an item to this collection, at the end.
     * @param x any object.
     * @return true.
     */
    public boolean add( AnyType x ) {
        add( size( ), x );   // index: size() = end of the list
        return true;         
    }
    
    /**
     * Adds an item to this collection, at specified position.
     * Items at or after that position are slid one position higher.
     * @param x any object.
     * @param idx position to add at.
     * @throws IndexOutOfBoundsException if idx is not between 0 and size(), inclusive.
     */
    public void add( int idx, AnyType x ) {
        addBefore( getNode( idx, 0, size( ) ), x ); // plugs in new node before node at index idx
    }
    
    /**
     * Adds an item to this collection, at specified position p.
     * Items at or after that position are slid one position higher.
     * @param p Node to add before.
     * @param x any object.
     * @throws IndexOutOfBoundsException if idx is not between 0 and size(), inclusive.
     */    
    private void addBefore( Node<AnyType> p, AnyType x ) {
        Node<AnyType> newNode = new Node<>( x, p.prev, p );
        newNode.prev.next = newNode;
        p.prev = newNode;         
        theSize++;
        modCount++;
    }   
    
    
    /**
     * Returns the item at position idx.
     * @param idx the index to search in.
     * @throws IndexOutOfBoundsException if index is out of range.
     */
    public AnyType get( int idx ) {
        return getNode( idx ).data;
    }
        
    /**
     * Changes the item at position idx.
     * @param idx the index to change.
     * @param newVal the new value.
     * @return the old value.
     * @throws IndexOutOfBoundsException if index is out of range.
     */
    public AnyType set( int idx, AnyType newVal ) {
        Node<AnyType> p = getNode( idx );
        AnyType oldVal = p.data;
        
        p.data = newVal;   
        return oldVal;
    }
    
    /**
     * Gets the Node at position idx, which must range from 0 to size( ) - 1.
     * @param idx index to search at.
     * @return internal node corresponding to idx.
     * @throws IndexOutOfBoundsException if idx is not between 0 and size( ) - 1, inclusive.
     */
    private Node<AnyType> getNode( int idx ) {
        return getNode( idx, 0, size( ) - 1 );
    }

    /**
     * Gets the Node at position idx, which must range from lower to upper.
     * @param idx index to search at.
     * @param lower lowest valid index.
     * @param upper highest valid index.
     * @return internal node corresponding to idx.
     * @throws IndexOutOfBoundsException if idx is not between lower and upper, inclusive.
     */    
    private Node<AnyType> getNode( int idx, int lower, int upper ) {
        // Lower and upper parameters can be useful for other functionalities such as implementing binary search
        Node<AnyType> p;
        
        if( idx < lower || idx > upper )
            throw new IndexOutOfBoundsException( "getNode index: " + idx + "; size: " + size( ) );
            
        if( idx < size( ) / 2 ) { // search from the front
            p = beginMarker.next;
            for( int i = 0; i < idx; i++ )
                p = p.next;            
        } else {    // search from the end
            p = endMarker;
            for( int i = size( ); i > idx; i-- )
                p = p.prev;
        } 
        
        return p;
    }
    
    /**
     * Removes an item from this collection.
     * @param idx the index of the object.
     * @return the item was removed from the collection.
     */
    public AnyType remove( int idx ) {
        return remove( getNode( idx ) );
    }
   
    /*public int find(AnyType x) {
        int idx = 0;
        for (AnyType element : this) {
            if (element.equals(x))
                return idx;
        }
        return -1;
    }*/
 
    /**
     * Removes the object contained in Node p.
     * @param p the Node containing the object.
     * @return the item was removed from the collection.
     */
    private AnyType remove( Node<AnyType> p ) {
        p.next.prev = p.prev;
        p.prev.next = p.next;
        theSize--;
        modCount++;
       
        p.next = null;
        p.prev = null; 
        return p.data;
    }
    
}
```

---

## For-Each Loops

Also called an enhanced for-loop.

Works by obtaining an object called an `Iterator ` then calling `next()` on the `Iterator` to obtain the next object.

## Iterator

Sometimes called the Iterator protocol.

```java
package java.util; 

interface Iterator<T> {
	boolean hasNext();
	T next();
	void remove();
}
```

`Iterator` is an **interface** that requires three different methods: 

- `hasNext`: Returns true if there's another element in the iteration
- `next`: Returns the next element in the iteration
- `remove`: Removes element

Goal: Make our `List` implementation compatible with the `Iterator` interface so we can loop through the `List` using an enhanced for loop.

## Iterable Interface

```java
package java.lang; // java.lang imported by default

interface Iterable<T> {
	Iterator<T> iterator();
}
```


Using `Iterables` and `Iterators`:

```java
Iterator<T> someIterator = someIterable.iterator();

while (someIterator.hasNext()) {
	T nextItem = someIterator.next();
	System.out.println(nextItem.toString());
}
```

- *What an enhanced for loop is doing*

Our lists will be Iterables and the iterator needs to iterate the same type of object as the iterable.

*WARNING: Never implement `Iterable` and `Iterator` in the same class!*

- So you can have different iterators, for when you're looping through nested for-loops, for example.

==Implementing Iterable and Iterator within our Array List:==

```java
import java.util.Iterator;
//import java.lang.Iterable; // don't have to import java.lang

public class MyArrayList<AnyType> implements List<AnyType>, Iterable<AnyType>{

    private static final int DEFAULT_CAPACITY = 10;
    
    private AnyType [ ] theItems;
    private int theSize;

    /**
     * Construct an empty ArrayList.
     */
    public MyArrayList() {
        clear();
    }
   
    /**
     * Change the size of this list to zero.
     */
    public void clear( ) {
        theSize = 0;
        ensureCapacity( DEFAULT_CAPACITY );
    }

    /**
     * @return the number of items in this list. 
     */
    public int size( ) {
        return theSize;
    }
    
    /**
     * @return true if this list is empty.
     */ 
    public boolean isEmpty( ) {
        return size( ) == 0;
    }
    
    /**
     * @return the item at position idx.
     * @param idx the index to search in.
     * @throws ArrayIndexOutOfBoundsException if index is out of range.
     */
    public AnyType get( int idx ) {
        if( idx < 0 || idx >= size() )
            throw new ArrayIndexOutOfBoundsException( "Index " + idx + "; size " + size( ) );
        return theItems[ idx ];    
    }
        
    /**
     * Changes the item at position idx.
     * @param idx the index to change.
     * @param newVal the new value.
     * @return the old value.
     * @throws ArrayIndexOutOfBoundsException if index is out of range.
     */
    public AnyType set( int idx, AnyType newVal ) {
        if( idx < 0 || idx >= size( ) )
            throw new ArrayIndexOutOfBoundsException( "Index " + idx + "; size " + size( ) );
        AnyType old = theItems[ idx ];    
        theItems[ idx ] = newVal;
        
        return old;    
    }

    /**
    * Adds an item to this list, at the end.
    * @param x any object.
    * @return true.
    */
    public boolean add( AnyType x ) {
    add( size(), x );
       return true;            
    }

    /**
    * Adds an item to this list, at the specified index.
    * @param x any object.
    * @return true.
    */
    public void add( int idx, AnyType x ) {
       if( theItems.length == size( ) )
           ensureCapacity( size() * 2 + 1 );

       for( int i = theSize; i > idx; i-- )
           theItems[ i ] = theItems[ i - 1 ];

       theItems[ idx ] = x;
       theSize++;  
    }
 
    /**
    * Removes an item from this list.
    * @param idx the index of the object.
    * @return the item was removed from the list.
    */
    public AnyType remove( int idx ) {
       AnyType removedItem = theItems[ idx ];
       
       for( int i = idx; i < size( ) - 1; i++ )
           theItems[ i ] = theItems[ i + 1 ];
       theSize--;    
       
       return removedItem;
    }

    /**
    * Returns a String representation of this list.
    */
    @Override
    public String toString( ) {
       StringBuilder sb = new StringBuilder( "[ " );
      
       for(int i=0; i < theSize; i++) 
           sb.append( theItems[i] + " " );
       sb.append( "]" );

       return new String(sb);
    }

    private void ensureCapacity( int newCapacity ) {
        if( newCapacity < theSize )
            return;

        AnyType [ ] old = theItems;
        theItems = (AnyType[ ]) new Object[ newCapacity ];
        // can't instantiate new array of a generic type since Java needs to know how much memory to allocate to the array. So we create an array of Objects then downcast it into an array of generic type
        // Generics in java exist only in compile time, not in runtime. When the code is compiled, all the generic types become objects
        for( int i = 0; i < size( ); i++ )
            theItems[ i ] = old[ i ];
    }

    public Iterator<AnyType> iterator() {
    
      return new ArrayListIterator(); 
      //return this;

    }

    private class ArrayListIterator implements Iterator<AnyType> {
    // inner class are able to access the private variables of the surrounding class if they're not declared static

      int current = 0;      // starts at 0 because index 0 is start of ArrayList

      public boolean hasNext(){
          return current < theSize; //size();
      }

      public AnyType next() {
//        AnyType result = get(current);
//        current++;
//        return result;    equivalent of return get(current++);
        return get(current++);
      }

      public void remove() {
      }

    }

    public static void main(String[] argv){
        
        MyArrayList<Integer> list = new MyArrayList<Integer>();
        list.add(1);
        list.add(2);
        list.add(3);
        
       for (Integer element : list) {
          for (Integer element2 : list) {
            System.out.print(element);
            System.out.print(" ");
            System.out.println(element2);
          }
       }

//        Iterator<Integer> iter = list.iterator();
//        while (iter.hasNext()) {
//            Integer element = iter.next();
//            System.out.println(element);
//        } // What the enhanced for loop translates to

    }

}
```

==Benefits of using an iterator:==

Using a for loop:

```java
int total = 0;
for (int i=0; i<list.size();i++) {
	total = total + list.get(i);
}
```

- If list is an ArrayList, runtime = n
- If list is a LinkedList, runtime = n^2^ since `get(i)` will take n time in the worst case

Using an enhanced for loop which uses an iterator:

```java
int total = 0;
for (Integer element : list) {
	total = total + element; 
}
```

- Both ArrayList and LinkedList will run in n time
  - Iterator will use next reference for LinkedList and index++ for ArrayList

==Iterator for LinkedList:==

```java
private class LinkedListIterator implements Iterator<AnyType> {
	int current = beginMarker.next;
	
	public boolean hasNext() {
		return current != endMarker;
	}
	
	public AnyType next() {
		AnyType result = current.data;
		current = current.next;
		return result;
	}
	
	public void remove() {}
}
```

