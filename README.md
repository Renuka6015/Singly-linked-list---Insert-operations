# Singly-linked-list---Insert-operations
This is to know about how insertion takes place in Singly Linked List.

class Node{
    int data;
    Node next;
    //Constructor
    Node(int data){
        this.data = data;
        this.next = null;
    }
}

class SinglyLinkedList{
    Node head;
    //To Insert at Beginning
    public void insertAtBegin(int data){
        Node new_Node = new Node(data);
        new_Node.next = head;
        head = new_Node;
    }
    //To Insert at any Position
    public void insertAtPosition(int position,int data){
        if(position<=0){
            System.out.println("Invalid position");
            return;
        }
        Node newNode = new Node(data);
        if(position==1){
            newNode.next = head;
            head = newNode;
            return;
        }
        Node temp = head;
        for(int i = 0;i<position-1&&temp!=null;i++){
            temp = temp.next;
        }
        if(temp==null){
            System.out.println("Exceeds the given length.");
            return;
        }
        newNode.next = temp.next;
        temp.next = newNode;
        
    }
    //To insert at End
    public void insertAtEnd(int data){
         Node new_Node = new Node(data);
         
         //To check list is empty or not 
         if(head==null){
             head = new_Node;
             return;
         }
         
         //End logic
         Node temp = head;
         while(temp.next!= null){
             temp=temp.next;
         }
         temp.next = new_Node;
    }
    //To display the data
    public void display(){
        Node temp = head;
        if(temp==null){
            System.out.println("List is Empty");
        }
        while(temp!=null){
            
            System.out.print(temp.data);
            if(temp.next!=null){
                System.out.print("->");
            }
            temp = temp.next;
        }
        System.out.println(" ");
    }
}

class Main{
    public static void main(String[] args){
        SinglyLinkedList sll = new SinglyLinkedList();
        sll.insertAtBegin(1);
        sll.insertAtBegin(2);
        sll.insertAtBegin(3);
        sll.insertAtBegin(4);
        sll.insertAtBegin(5);
        sll.insertAtBegin(6);
        sll.display();
        sll.insertAtEnd(0);
        sll.insertAtEnd(-1);
        sll.insertAtEnd(-2);
        sll.display();
        sll.insertAtPosition(3,6);
        sll.display();
    }
}

OutPut:
6->5->4->3->2->1 
6->5->4->3->2->1->0->-1->-2 
6->5->4->6->3->2->1->0->-1->-2
