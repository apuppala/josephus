josephus
========

Homework
C:\Users\Abe\Desktop\Data Structure NA\Josephus.java

package josephus;

import java.util.*;
import java.until.LinkedList;
class Queue<T>
{
    private LinkedList <T> list;
    private int front;
    private int rear;
    
    public Queue()
    {
        list = new LinkedList<T>();
        front =0;
        rear=0;
    }
    
    public void insert(T item)
    {
        list.addLast(item);
        rear++;
    }
    
    public T delete()
    {
        T item;
        if (isEmpty())
                {
                    System.out.print("EMPTY!!");
                    return null;
                }
        else{
            item=list.removeFirst();
            front++;
        }
        return item;
    }
    public T getFrist()
    {
     T item=null;
     if (!isEmpty())
         item=list.getfirst();
     return item;
    }
    
    public T getLast()
    {
        T item=null;
        if (!isEmpty())
            item=list.getLast();
        return item;
    }
    
    public boolean isEmpty()
    {
        return front==rear;
    }
    public int QueueSize()
    {
        return list.size();
    }
    public void dispay()
    {
        for (T e:list)
            System.out.println(e);
    }
}

/**
* Demonstrates the use of an indexed list to solve the Josephus problem.
*
* @author Lewis and Chase
* @version 4.0
*/
public class Josephus 
{
/**
* Continue around the circle eliminating every nth soldier 
* until all of the soldiers have been eliminated.
     * @param args
*/
    public static void main(String[] args)
    {
    int numPeople, skip, targetIndex;
    Queue<Integer> queue = new Queue<Integer>();
    Scanner in = new Scanner(System.in);
    // get the initial number of soldiers 
    System.out.print("Enter the number of soldiers: ");
    numPeople = in.nextInt();
    in.nextLine(); 
    // get the number of soldiers to skip 
    System.out.print("Enter the number of soldiers to skip: ");
    skip = in.nextInt(); 
    //Java Software Structures, 4th Edition, Lewis/Chase 6 - 30// load the initial list of soldiers 
    for (int count = 1; count <= numPeople; count++)
    {
    queue.add("Soldier " + count);
    }
    targetIndex = skip; 
    System.out.println("The order is: ");
    // Treating the list as circular, remove every nth element
    // until the list is empty 
    while (!queue.isEmpty()) 
    {
    System.out.println(queue.remove(targetIndex));
    if (queue.size() > 0)
    targetIndex = (targetIndex + skip) % queue.size();
    }
    }
}
