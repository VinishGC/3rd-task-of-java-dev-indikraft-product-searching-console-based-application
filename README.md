//# 3rd-task-of-java-dev-indikraft-product-searching-console-based-application
//file name ProductSearch.java
import java.util.*;

class Product {
    String name;
    double price;

    Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String toString() {
        return name + " Rs." + price;
    }
}

public class ProductSearch {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        
        List<Product> products = new ArrayList<>();
        products.add(new Product("Laptop", 55000));
        products.add(new Product("Mobile", 15000));
        products.add(new Product("Headphones", 2000));
        products.add(new Product("Mouse", 500));
        products.add(new Product("Keyboard", 1200));

        while (true) {
            System.out.println("\n=== Product Search Menu ===");
            System.out.println("1. Search by name");
            System.out.println("2. Search by price range");
            System.out.println("3. View all products");
            System.out.println("4. Exit");
            System.out.print("Enter choice: ");
            int choice = sc.nextInt();
            sc.nextLine(); 
        

            if (choice == 1) {
                System.out.print("Enter product name to search: ");
                String keyword = sc.nextLine().toLowerCase();
                products.stream()
                        .filter(p -> p.name.toLowerCase().contains(keyword))
                        .forEach(System.out::println);

            } else if (choice == 2) {
                System.out.print("Enter min price: ");
                double min = sc.nextDouble();
                System.out.print("Enter max price: ");
                double max = sc.nextDouble();
                products.stream()
                        .filter(p -> p.price >= min && p.price <= max)
                        .forEach(System.out::println);

            } else if (choice == 3) {
                products.forEach(System.out::println);

            } else if (choice == 4) {
                System.out.println("Thank you !!");
                break;

            } else {
                System.out.println("Invalid choice! Try again.");
            }
        }
        sc.close();
    }
}
