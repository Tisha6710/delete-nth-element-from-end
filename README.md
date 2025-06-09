# delete-nth-element-from-end
package LinkedList;

public class deleteNthfromend {

    // Delete nth node from end and return new head
    public static Node delete(Node head, int n) {
        Node slow = head;
        Node fast = head;

        // Move fast n steps ahead
        for (int i = 1; i <= n; i++) {
            fast = fast.next;
        }

        // If fast == null → delete head node
        if (fast == null) {
            return head.next;
        }

        // Move slow and fast till fast.next == null
        while (fast.next != null) {
            slow = slow.next;
            fast = fast.next;
        }

        // Delete nth node from end
        slow.next = slow.next.next;

        return head;
    }

    public static void display(Node head) {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
        }
    }

    public static void main(String[] args) {
        Node a = new Node(100);
        Node b = new Node(13);
        Node c = new Node(12);
        Node d = new Node(4);
        Node e = new Node(5);
        Node f = new Node(10);
        a.next = b;
        b.next = c;
        c.next = d;
        d.next = e;
        e.next = f;

        display(a);
        a = delete(a, 6); // 👈 Yeh zaroori hai
        display(a);
    }
}



