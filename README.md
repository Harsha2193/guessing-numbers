# guessing-numbers
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        // Define the range for the random number
        int lowerBound = 1;
        int upperBound = 100;
        
        // Generate a random number between lowerBound and upperBound
        int numberToGuess = random.nextInt(upperBound - lowerBound + 1) + lowerBound;
        int userGuess = 0;
        int numberOfTries = 0;
        boolean hasGuessedCorrectly = false;
        
        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("Guess the number between " + lowerBound + " and " + upperBound + ":");
        
        // Game loop
        while (!hasGuessedCorrectly) {
            try {
                // Get user input
                userGuess = Integer.parseInt(scanner.nextLine());
                numberOfTries++;
                
                // Check if the guess is correct
                if (userGuess < lowerBound || userGuess > upperBound) {
                    System.out.println("Please guess a number between " + lowerBound + " and " + upperBound + ".");
                } else if (userGuess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else if (userGuess > numberToGuess) {
                    System.out.println("Too high! Try again.");
                } else {
                    hasGuessedCorrectly = true;
                    System.out.println("Congratulations! You guessed the number in " + numberOfTries + " tries.");
                }
                
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a number.");
            }
        }
        
        scanner.close();
    }
}
