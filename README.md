# prework_august30-knesada
prework_august30-knesada created by GitHub Classroom
package nyc.c4q;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        boolean play = true;

        while (play) {
            Hangman hangman = new Hangman();
            while (hangman.getMisses() < 5) {
                hangman.printCurrentWord();
                hangman.promptPlayer("Enter a letter: ");
                hangman.readLetter();
                hangman.checkLetter();
                if (hangman.guessedSuccessfully()) {
                    break;
                }
                System.out.println(Drawing.get(hangman.getMisses()));
                System.out.println("Misses -> " + hangman.getMisses());
            }
            if (hangman.guessedSuccessfully()) {
                System.out.println("Success");
            } else {
                System.out.println("The answer was " + hangman.getSecretWord());
            }

            System.out.println("Play again? (yes/no)");

            boolean validAnswer = false;
            do {
                Scanner in = new Scanner(System.in);
                String answer = in.next();
                answer = answer.toLowerCase();
                if (answer.equals("yes") || answer.equals("y")) {
                    play = true;
                    validAnswer = true;
                } else if (answer.equals("no")|| answer.equals("n")){
                    play = false;
                    validAnswer = true;
                } else {
                    System.out.println("Please answer with yes or no. Thank You!");
                }
            }while (validAnswer == false);
        }
    }
}
