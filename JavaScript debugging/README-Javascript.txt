Sample of Properly Formatted CODE
----------------------------------------
// ---------------------------------------------
// Project: Quick Quiz
// Student: Jessica Salazar
// Date: February 16, 2026
// Description: A simple console quiz that asks multiple-choice questions,
//              validates input, tracks score, and offers replay.
// ---------------------------------------------

// This class represents a single quiz question with choices and the correct answer index.
public class Question {
    private final String text;
    private final java.util.List<String> choices;
    private final int correct Index;

    public Question(String text, java.util.List<String> choices, int correct Index) {
        this. Text = text;
        this. Choices = choices;
        this.correctIndex = correct Index;
    }

    public String get Text() { return text; }
    public java.util.List<String> get Choices() { return choices; }
    public int getCorrectIndex() { return correct Index; }
}

// This method runs one quiz session: it displays each question, reads the user's choice,
// validates the input, provides immediate feedback, and returns the final score.
public static int run Quiz(java.util.Scanner scanner, java.util.List<Question> questions) {
    int score = 0;

    for (Question q : questions) {
        System.out.println("Q: " + q.getText());
        java.util.List<String> opts = q.getChoices();
        for (int i = 0; i < opts.size(); i++) {
            System.out.println("  " + (i + 1) + ". " + opts. Get(i));
        }

        Integer selection = null;
        // We ask the user for a valid number until a proper selection is made
        while (selection == null) {
            System.out.print("Select an option (1-" + opts. Size() + "): ");
            String raw = scanner.nextLine().trim();
            try {
                int n = Integer.parseInt(raw);
                if (n >= 1 && n <= opts. Size()) {
                    selection = n - 1; // convert to 0-based index
                } else {
                    System.out.println("Please enter a number between 1 and " + opts. Size() + ".");
                }
            } catch (NumberFormatException ex) {
                System.out.println("Please enter a valid number.");
            }
        }

        // We check the answer and update the score
        if (selection == q.getCorrectIndex()) {
            score++;
            System.out.println("Correct!");
        } else {
            System.out.println("Incorrect. Correct answer: " + opts. Get(q.getCorrectIndex()));
        }
        System.out.println();
    }

    // Finally, we display the results to the screen
    System.out.println("Quiz complete! Your score: " + score + " / " + questions. Size());
    return score;
}

// sample code ends above //