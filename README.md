import java.util.Scanner;

public class Calculator {

    // Method to display the menu
    public static void showMenu() {
        System.out.println("\n==== Calculator Menu ====");
        System.out.println("1. Addition (+)");
        System.out.println("2. Subtraction (-)");
        System.out.println("3. Multiplication (*)");
        System.out.println("4. Division (/)");
        System.out.println("5. Exit");
        System.out.print("Choose an option (1-5): ");
    }

    // Method to perform the selected operation
    public static double performOperation(int choice, double num1, double num2) {
        switch (choice) {
            case 1:
                return num1 + num2;
            case 2:
                return num1 - num2;
            case 3:
                return num1 * num2;
            case 4:
                if (num2 == 0) {
                    System.out.println("Error: Cannot divide by zero.");
                    return Double.NaN;
                } else {
                    return num1 / num2;
                }
            default:
                System.out.println("Invalid operation.");
                return Double.NaN;
        }
    }

    // Main method
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean keepRunning = true;

        System.out.println("Welcome to Java Console Calculator!");

        while (keepRunning) {
            showMenu();

            int choice;
            try {
                choice = Integer.parseInt(scanner.nextLine());
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a number between 1 and 5.");
                continue;
            }

            if (choice == 5) {
                System.out.println("Exiting... Thank you for using the calculator.");
                keepRunning = false;
                continue;
            }

            double num1, num2;

            try {
                System.out.print("Enter first number: ");
                num1 = Double.parseDouble(scanner.nextLine());

                System.out.print("Enter second number: ");
                num2 = Double.parseDouble(scanner.nextLine());
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter numeric values.");
                continue;
            }

            double result = performOperation(choice, num1, num2);
            if (!Double.isNaN(result)) {
                System.out.println("Result: " + result);
            }
        }

        scanner.close();
    }
}

