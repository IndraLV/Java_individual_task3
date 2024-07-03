# Java_individual_task3
## This was crazy! I was on vacation with family than returned and tried to manage 2 lessons, test and individual task... So much errors, corrections, interesting advices fro AI like never before. 
## I am not satisfied with result, but deadline is close so...
## Hope to be better next time!

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        CheeseShop cheeseShop = new CheeseShop();
        Scanner scanner = new Scanner(System.in);
        String choice;

        while (true) {
            System.out.println("To add cheese to shop, press 1!");
            System.out.println("To remove cheese from shop, press 2!");
            System.out.println("To see list of available cheeses, press 3!");
            System.out.println("To add cheese to cart, press 4!");
            System.out.println("To remove cheese from cart, press 5!");
            System.out.println("To see cart, press 6!");
            System.out.println("To finish, press 7!");

            choice = scanner.nextLine();

            if (choice.equals("1")) {
                System.out.print("Enter cheese name: ");
                String name = scanner.nextLine();
                System.out.print("Enter cheese price: ");
                double price = Double.parseDouble(scanner.nextLine());
                cheeseShop.addCheeseToShop(new Cheese(name, price));
                System.out.println("Cheese added!");
            } else if (choice.equals("2")) {
                System.out.print("Enter cheese name to remove: ");
                String name = scanner.nextLine();
                cheeseShop.removeCheeseFromShop(name);
                System.out.println("Cheese removed!");
            } else if (choice.equals("3")) {
                System.out.println("Available cheeses:");
                for (Cheese cheese : cheeseShop.getCheesesAvailable()) {
                    System.out.println(cheese);
                }
            } else if (choice.equals("4")) {
                System.out.print("Enter cheese name to add to cart: ");
                String name = scanner.nextLine();
                cheeseShop.addToCart(name);
            } else if (choice.equals("5")) {
                System.out.print("Enter cheese name to remove from cart: ");
                String name = scanner.nextLine();
                cheeseShop.removeFromCart(name);
            } else if (choice.equals("6")) {
                System.out.println("In cart you have:");
                for (Cheese cheese : cheeseShop.getCart()) {
                    System.out.println(cheese);
                }
            } else if (choice.equals("7")) {
                System.out.println("See you next time!");
                scanner.close();
                return;
            } else {
                System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
```

```java
import java.util.ArrayList;
import java.util.List;


class CheeseShop {
    private List<Cheese> cheeses = new ArrayList<>();
    private List<Cheese> cart = new ArrayList<>();


    public void addCheeseToShop(Cheese cheese) {
        cheeses.add(cheese);
    }


    public void removeCheeseFromShop(String name) {
        cheeses.removeIf(cheese -> cheese.getName().equals(name));
    }


    public void addToCart(String name) {
        Cheese cheese = findCheeseInShop(name);
        if (cheese != null) {
            cart.add(cheese);
            System.out.println("Added to cart: " + cheese);
        } else {
            System.out.println("Cheese not found in shop!");
        }
    }


    public void removeFromCart(String name) {
        cart.removeIf(cheese -> cheese.getName().equals(name));
        System.out.println("Removed from cart: " + name);
    }


    public List<Cheese> getCheesesAvailable() {
        return new ArrayList<>(cheeses);
    }


    public List<Cheese> getCart() {
        return new ArrayList<>(cart);
    }


    public Cheese findCheeseInShop(String name) {
        for (Cheese cheese : cheeses) {
            if (cheese.getName().equals(name)) {
                return cheese;
            }
        }
        return null;
    }
}
```

```java
class Cheese {
    private String name;
    private double price;

    public Cheese(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }


}
```

