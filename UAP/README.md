# SD

#### MODUL 1 - GENERICS JAVA
```java
import java.util.ArrayList;
import java.util.Scanner;

public class GenericCollectionBox<T> {
    private ArrayList<T> items = new ArrayList<>();
    private Scanner scanner = new Scanner(System.in);

    public void addItem(T item) {
        items.add(item);
    }

    public void displayItems() {
        if (items.isEmpty()) {
            System.out.println("Kotak kosong!");
        } else {
            System.out.println("Isi kotak: " + items);
        }
    }

    public void run() {
        while (true) {
            System.out.println("\n1. Tambah Item");
            System.out.println("2. Tampilkan Item");
            System.out.println("3. Keluar");
            System.out.print("Pilih opsi: ");
            int choice = scanner.nextInt();
            scanner.nextLine();

            if (choice == 1) {
                System.out.print("Masukkan item (String atau Angka): ");
                String input = scanner.nextLine();
                try {
                    int num = Integer.parseInt(input);
                    addItem((T) Integer.valueOf(num));
                } catch (NumberFormatException e) {
                    addItem((T) input);
                }
            } else if (choice == 2) {
                displayItems();
            } else if (choice == 3) {
                System.out.println("Keluar dari program.");
                break;
            } else {
                System.out.println("Pilihan tidak valid!");
            }
        }
        scanner.close();
    }

    public static void main(String[] args) {
        GenericCollectionBox<Object> box = new GenericCollectionBox<>();
        box.run();
    }
}
```

#### MODUL 2 - ARRAY LIST & LINKED LIST
```java
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Scanner;

public class ShoppingListManager {
    private ArrayList<String> arrayList = new ArrayList<>();
    private LinkedList<String> linkedList = new LinkedList<>();
    private boolean useArrayList = true;
    private Scanner scanner = new Scanner(System.in);

    public void addItem(String item) {
        if (useArrayList) arrayList.add(item);
        else linkedList.add(item);
    }

    public void removeItem(int index) {
        if (useArrayList && !arrayList.isEmpty()) arrayList.remove(index);
        else if (!linkedList.isEmpty()) linkedList.remove(index);
    }

    public void displayList() {
        System.out.println("Daftar Belanjaan (" + (useArrayList ? "ArrayList" : "LinkedList") + "):");
        if (useArrayList) System.out.println(arrayList);
        else System.out.println(linkedList);
    }

    public void run() {
        while (true) {
            System.out.println("\n1. Tambah Item");
            System.out.println("2. Hapus Item");
            System.out.println("3. Tampilkan Daftar");
            System.out.println("4. Ganti Tipe List");
            System.out.println("5. Keluar");
            System.out.print("Pilih opsi: ");
            int choice = scanner.nextInt();
            scanner.nextLine();

            if (choice == 1) {
                System.out.print("Masukkan item belanjaan: ");
                addItem(scanner.nextLine());
            } else if (choice == 2) {
                System.out.print("Masukkan indeks item untuk dihapus: ");
                int index = scanner.nextInt();
                removeItem(index);
            } else if (choice == 3) {
                displayList();
            } else if (choice == 4) {
                useArrayList = !useArrayList;
                System.out.println("Tipe list diubah ke " + (useArrayList ? "ArrayList" : "LinkedList") + ".");
            } else if (choice == 5) {
                System.out.println("Keluar dari program.");
                break;
            } else {
                System.out.println("Pilihan tidak valid!");
            }
        }
        scanner.close();
    }

    public static void main(String[] args) {
        ShoppingListManager manager = new ShoppingListManager();
        manager.run();
    }
}
```
#### MODUL 3 - STACK & QUEUE
```java
import java.util.Stack;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class RestaurantQueue {
    private Queue<String> orderQueue = new LinkedList<>();
    private Stack<String> returnStack = new Stack<>();
    private Scanner scanner = new Scanner(System.in);

    public void addOrder(String order) {
        orderQueue.offer(order);
    }

    public void processOrder() {
        if (!orderQueue.isEmpty()) {
            System.out.println("Pesanan diproses: " + orderQueue.poll());
        } else {
            System.out.println("Antrian kosong!");
        }
    }

    public void returnOrder(String order) {
        returnStack.push(order);
    }

    public void displayStatus() {
        System.out.println("Antrian Pesanan: " + orderQueue);
        System.out.println("Pesanan Kembali: " + returnStack);
    }

    public void run() {
        while (true) {
            System.out.println("\n1. Tambah Pesanan");
            System.out.println("2. Proses Pesanan");
            System.out.println("3. Kembalikan Pesanan");
            System.out.println("4. Tampilkan Status");
            System.out.println("5. Keluar");
            System.out.print("Pilih opsi: ");
            int choice = scanner.nextInt();
            scanner.nextLine();

            if (choice == 1) {
                System.out.print("Masukkan nama pesanan: ");
                addOrder(scanner.nextLine());
            } else if (choice == 2) {
                processOrder();
            } else if (choice == 3) {
                System.out.print("Masukkan nama pesanan yang dikembalikan: ");
                returnOrder(scanner.nextLine());
            } else if (choice == 4) {
                displayStatus();
            } else if (choice == 5) {
                System.out.println("Keluar dari program.");
                break;
            } else {
                System.out.println("Pilihan tidak valid!");
            }
        }
        scanner.close();
    }

    public static void main(String[] args) {
        RestaurantQueue queue = new RestaurantQueue();
        queue.run();
    }
}
```
#### MODUL 4 - HASHMAP
```java
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class PhoneBook {
    private Map<String, String> phoneBook = new HashMap<>();
    private Scanner scanner = new Scanner(System.in);

    public void addContact(String name, String number) {
        phoneBook.put(name, number);
    }

    public void findContact(String name) {
        String number = phoneBook.get(name);
        if (number != null) {
            System.out.println("Nomor " + name + ": " + number);
        } else {
            System.out.println("Kontak tidak ditemukan!");
        }
    }

    public void removeContact(String name) {
        if (phoneBook.remove(name) != null) {
            System.out.println("Kontak " + name + " dihapus!");
        } else {
            System.out.println("Kontak tidak ditemukan!");
        }
    }

    public void run() {
        while (true) {
            System.out.println("\n1. Tambah Kontak");
            System.out.println("2. Cari Kontak");
            System.out.println("3. Hapus Kontak");
            System.out.println("4. Keluar");
            System.out.print("Pilih opsi: ");
            int choice = scanner.nextInt();
            scanner.nextLine();

            if (choice == 1) {
                System.out.print("Masukkan nama: ");
                String name = scanner.nextLine();
                System.out.print("Masukkan nomor telepon: ");
                String number = scanner.nextLine();
                addContact(name, number);
            } else if (choice == 2) {
                System.out.print("Masukkan nama untuk dicari: ");
                findContact(scanner.nextLine());
            } else if (choice == 3) {
                System.out.print("Masukkan nama untuk dihapus: ");
                removeContact(scanner.nextLine());
            } else if (choice == 4) {
                System.out.println("Keluar dari program.");
                break;
            } else {
                System.out.println("Pilihan tidak valid!");
            }
        }
        scanner.close();
    }

    public static void main(String[] args) {
        PhoneBook book = new PhoneBook();
        book.run();
    }
}
```
#### MODUL 5 - TREE
```java
import java.util.Scanner;

public class InteractiveFamilyTree {
    static class Node {
        String name;
        Node left, right;

        public Node(String name) {
            this.name = name;
            this.left = null;
            this.right = null;
        }
    }

    private Node root;
    private Scanner scanner = new Scanner(System.in);

    public void addMember(String name, String parentName) {
        if (root == null) {
            root = new Node(name);
            return;
        }
        addMemberRec(root, name, parentName);
    }

    private void addMemberRec(Node node, String name, String parentName) {
        if (node.name.equals(parentName)) {
            if (node.left == null) node.left = new Node(name);
            else if (node.right == null) node.right = new Node(name);
        } else {
            if (node.left != null) addMemberRec(node.left, name, parentName);
            if (node.right != null) addMemberRec(node.right, name, parentName);
        }
    }

    public void displayTree() {
        System.out.println("\nPohon Keluarga:");
        displayTreeRec(root, "", true);
    }

    private void displayTreeRec(Node node, String prefix, boolean isTail) {
        if (node != null) {
            System.out.println(prefix + (isTail ? "└── " : "├── ") + node.name);
            displayTreeRec(node.left, prefix + (isTail ? "    " : "│   "), false);
            displayTreeRec(node.right, prefix + (isTail ? "    " : "│   "), true);
        }
    }

    public void run() {
        System.out.print("Masukkan nama Kepala Keluarga: ");
        String rootName = scanner.nextLine();
        root = new Node(rootName);

        while (true) {
            System.out.println("\n1. Tambah Anggota");
            System.out.println("2. Tampilkan Pohon");
            System.out.println("3. Keluar");
            System.out.print("Pilih opsi: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Bersihkan buffer

            if (choice == 1) {
                System.out.print("Masukkan nama anggota: ");
                String name = scanner.nextLine();
                System.out.print("Masukkan nama orang tua: ");
                String parentName = scanner.nextLine();
                addMember(name, parentName);
            } else if (choice == 2) {
                displayTree();
            } else if (choice == 3) {
                System.out.println("Keluar dari program.");
                break;
            } else {
                System.out.println("Pilihan tidak valid!");
            }
        }
        scanner.close();
    }

    public static void main(String[] args) {
        InteractiveFamilyTree tree = new InteractiveFamilyTree();
        tree.run();
    }
}
```
#### MODUL 6 - GRAPH
```java
import java.util.ArrayList;
import java.util.List;

public class GraphDemo {
    private int V;
    private List<List<Integer>> adjList;

    public GraphDemo(int v) {
        V = v;
        adjList = new ArrayList<>(v);
        for (int i = 0; i < v; i++) {
            adjList.add(new ArrayList<>());
        }
    }

    public void addEdge(int src, int dest) {
        adjList.get(src).add(dest);
        adjList.get(dest).add(src);
    }

    public void printGraph() {
        for (int i = 0; i < V; i++) {
            System.out.print("Vertex " + i + " terhubung dengan: ");
            for (int j : adjList.get(i)) {
                System.out.print(j + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        GraphDemo graph = new GraphDemo(4);
        graph.addEdge(0, 1); // Budi - Andi
        graph.addEdge(0, 2); // Budi - Siti
        graph.addEdge(1, 3); // Andi - Rina
        graph.printGraph();
    }
}
```
-----
```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import java.util.Scanner;

public class SimpleGraph<T> {

    private final Map<T, List<T>> adjacencyList;

    public SimpleGraph() {
        this.adjacencyList = new HashMap<>();
    }

    public void addVertex(T vertex) {
        adjacencyList.putIfAbsent(vertex, new ArrayList<>());
    }

    public void addEdge(T vertex1, T vertex2) {
        addVertex(vertex1);
        addVertex(vertex2);
        adjacencyList.get(vertex1).add(vertex2);
        adjacencyList.get(vertex2).add(vertex1);
    }

    public void printGraph() {
        System.out.println("\n--- Struktur Graph (Adjacency List) ---");
        if (adjacencyList.isEmpty()) {
            System.out.println("Graph masih kosong.");
            return;
        }
        for (T vertex : adjacencyList.keySet()) {
            System.out.println("Vertex '" + vertex + "' terhubung dengan: " + adjacencyList.get(vertex));
        }
        System.out.println("----------------------------------------");
    }

    public static void main(String[] args) {
        SimpleGraph<String> socialNetwork = new SimpleGraph<>();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\n===== MENU PROGRAM GRAPH =====");
            System.out.println("1. Tambah Pengguna (Vertex)");
            System.out.println("2. Buat Pertemanan (Edge)");
            System.out.println("3. Tampilkan Seluruh Jaringan");
            System.out.println("4. Keluar");
            System.out.print("Pilih menu (1-4): ");

            String pilihan = scanner.nextLine();

            switch (pilihan) {
                case "1":
                    System.out.print("Masukkan nama pengguna baru: ");
                    String user = scanner.nextLine();
                    socialNetwork.addVertex(user);
                    System.out.println(">> Pengguna '" + user + "' berhasil ditambahkan.");
                    break;

                case "2":
                    System.out.print("Masukkan nama pengguna pertama: ");
                    String user1 = scanner.nextLine();
                    System.out.print("Masukkan nama pengguna kedua: ");
                    String user2 = scanner.nextLine();

                    if (user1.equalsIgnoreCase(user2)) {
                        System.out.println(">> Gagal: Pengguna tidak bisa berteman dengan dirinya sendiri.");
                        continue;
                    }

                    socialNetwork.addEdge(user1, user2);
                    System.out.println(">> Pertemanan antara '" + user1 + "' dan '" + user2 + "' berhasil dibuat.");
                    break;

                case "3":
                    socialNetwork.printGraph();
                    break;

                case "4":
                    System.out.println("Terima kasih telah menggunakan program ini. Sampai jumpa!");
                    scanner.close();
                    return;

                default:
                    System.out.println(">> Pilihan tidak valid. Silakan masukkan angka antara 1 sampai 4.");
                    break;
            }
        }
    }
}
```