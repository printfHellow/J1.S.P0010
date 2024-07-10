# J1.S.P0010
import java.util.*;

public class J1SP0010 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        // Prompt user to input the size of the array
        int size = getInput(scanner, "Enter number of array: ");

        // Prompt user to input the search number
        int searchNumber = getInput(scanner, "Enter the number to search: ");

        // Generate array with random integers
        int[] array = new int[size];
        System.out.println("The array:");
        for (int i = 0; i < size; i++) {
            array[i] = random.nextInt(10); // Generate random integer in range 0-9
            System.out.print(array[i] + " ");
        }
        System.out.println();

        // Perform linear search
        int index = linearSearch(array, searchNumber);

        // Display the result
        if (index != -1) {
            System.out.println("Number found at index: " + index);
        } else {
            System.out.println("Number not found in the array.");
        }

        scanner.close();
    }

    // Linear search function
    public static int linearSearch(int[] array, int searchNumber) {
        for (int i = 0; i < array.length; i++) {
            if (array[i] == searchNumber) {
                return i;
            }
        }
        return -1;
    }

    // Method to get and validate user input
    public static int getInput(Scanner scanner, String prompt) {
        int input = -1;
        boolean valid = false;
        while (!valid) {
            System.out.print(prompt);
            if (scanner.hasNextInt()) {
                input = scanner.nextInt();
                if (input >= 0) {
                    valid = true;
                } else {
                    System.out.println("Input must be a non-negative integer. Please try again.");
                }
            } else {
                System.out.println("Invalid input. Please enter an integer.");
                scanner.next(); // Clear the invalid input
            }
        }
        return input;
    }
}
