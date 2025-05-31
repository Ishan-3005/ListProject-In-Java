# ListProject-In-Java
import java.util.*;
class LinkedLists{
    Node head;
    class Node{
        String data;
        Node head;
        Node next;
        
        Node(String data){
            this.data = data;
            this.next = null;
        }
    }
    // Insertion In LinkedLists:-> 
    
    public void InsertFirst(String data) {
        Node newnode = new Node(data);
        if(head == null)
        {
            head = newnode;
            return;
        }
        newnode.next = head;
        head = newnode;
        
    }
    
    public void InsertBetween(String data, int index) {
        Node newnode = new Node(data);

        if (index < 1) {
            System.out.println("Invalid index.");
            return;
        }
        if (index == 1) {
            InsertFirst(data);
            return;
        }
        Node Temp_Node = head;
        int i = 0;
        while (Temp_Node != null && i < index - 1) {
            Temp_Node = Temp_Node.next;
            i++;
        }
        if (Temp_Node == null) {
            System.out.println("Index out of range.");
            return;
        }
        newnode.next = Temp_Node.next;
        Temp_Node.next = newnode;
    }

    
    public void InsertLast(String data){
        Node newnode = new Node(data);
        if(head == null)
        {
            head = newnode;
            return;
        }
        
        Node Temp_Node = head;
        while(Temp_Node.next != null)
        {
            Temp_Node = Temp_Node.next;
        }
        Temp_Node.next = newnode;
    }
    
    // Deletion In LinkedLists:->
    public void deleteFirst() {
        if (head == null) {
            System.out.println("List is empty:- ");
            return;
        }
        head = head.next;
        System.out.println("First element deleted.");
    }

    public void deleteLast() {
        if (head == null) {
            System.out.println("List is already empty.");
            return;
        }
        if (head.next == null) {
            head = null;
            System.out.println("Last element deleted.");
            return;
        }
        Node temp = head;
        while (temp.next.next != null) {
            temp = temp.next;
        }
        temp.next = null;
        System.out.println("Last element deleted.");
    }
    
    public void deleteAt(int index) {
        if (index < 0 || head == null) {
            System.out.println("Invalid operation.");
            return;
        }
        if (index == 0) {
            deleteFirst();
            return;
        }

        Node temp = head;
        int count = 0;
        while (temp != null && count < index - 1) {
            temp = temp.next;
            count++;
        }

        if (temp == null || temp.next == null) {
            System.out.println("Index out of range.");
            return;
        }

        temp.next = temp.next.next;
        System.out.println("Element at index " + index + " deleted.");
    }
    
    public void PrintList() {
        if(head == null)
        {
            System.out.println("List Is Empty:-> ");
        }
        Node Temp_Node = head;
        while(Temp_Node != null)
        {
            System.out.print("[" + Temp_Node.data + "]" + "-->");
            Temp_Node = Temp_Node.next;
        }
        System.out.println("Now Pointing to NULL");
    }
    
    public static void main(String[] args) {
        LinkedLists list = new LinkedLists();
        Scanner scanner = new Scanner(System.in);
        boolean running = true;

        System.out.println("===== Welcome to Linked List Program =====");

        while (running) {
            System.out.println("\nMain Menu:");
            System.out.println("1) Insert into Linked List");
            System.out.println("2) Delete from Linked List");
            System.out.println("3) Display Linked List");
            System.out.println("4) Exit");
            System.out.print("Enter your choice: ");
            
            int choice = scanner.nextInt();
            scanner.nextLine(); // consume newline

            switch (choice) {
                case 1:
                    System.out.println("\nInsert Options:");
                    System.out.println("1) Insert at Beginning");
                    System.out.println("2) Insert at Index");
                    System.out.println("3) Insert at End");
                    System.out.print("Enter your insertion choice: ");
                    int insertChoice = scanner.nextInt();
                    scanner.nextLine();

                    System.out.print("Enter data to insert: ");
                    String data = scanner.nextLine();

                    switch (insertChoice) {
                        case 1:
                            list.InsertFirst(data);
                            break;
                        case 2:
                            System.out.print("Enter index: ");
                            int index = scanner.nextInt();
                            list.InsertBetween(data, index);
                            break;
                        case 3:
                            list.InsertLast(data);
                            break;
                        default:
                            System.out.println("Invalid insertion choice.");
                    }
                    break;

                case 2:
                    System.out.println("\nDelete Options:");
                    System.out.println("1) Delete First Node");
                    System.out.println("2) Delete at Index");
                    System.out.println("3) Delete Last Node");
                    System.out.print("Enter your deletion choice: ");
                    int deleteChoice = scanner.nextInt();

                    switch (deleteChoice) {
                        case 1:
                            list.deleteFirst();
                            break;
                        case 2:
                            System.out.print("Enter index to delete: ");
                            int delIndex = scanner.nextInt();
                            list.deleteAt(delIndex);
                            break;
                        case 3:
                            list.deleteLast();
                            break;
                        default:
                            System.out.println("Invalid deletion choice.");
                    }
                    break;

                case 3:
                    System.out.println("\nCurrent Linked List:");
                    list.PrintList();
                    break;

                case 4:
                    running = false;
                    System.out.println("Exiting program. Thank you!");
                    break;

                default:
                    System.out.println("Invalid menu choice.");
            }
        }

        scanner.close();
    }
}
