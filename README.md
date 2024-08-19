# catalog-Hackathon
import java.util.*;

class Main {

    private static Map<String, String> stateCapitalMap = new HashMap<>();
    private static List<String> questions = new ArrayList<>();
    private static Scanner scanner = new Scanner(System.in);

   
    public static void addStateCapital(String state, String capital) {
        stateCapitalMap.put(state, capital);
    }

   
    public static String getRandomQuestion() {
        List<String> states = new ArrayList<>(stateCapitalMap.keySet());
        Random random = new Random();
        String state = states.get(random.nextInt(states.size()));
        return state;
    }

    public static void conductQuiz(int numQuestions) {
        int score = 0;

        for (int i = 0; i < numQuestions; i++) {
            String state = getRandomQuestion();
            String correctCapital = stateCapitalMap.get(state);

            System.out.println("What is the capital of " + state + "?");
            String userAnswer = scanner.nextLine().trim();

            if (userAnswer.equalsIgnoreCase(correctCapital)) {
                System.out.println("Correct!");
                score++;
            } else {
                System.out.println("Incorrect! The correct answer is " + correctCapital);
            }

            questions.add(state);
        }

        System.out.println("\nQuiz over! Your final score is: " + score + " out of " + numQuestions);
    }

  
    public static void main(String[] args) {
       
        addStateCapital("Karnataka", "Bengaluru");
        addStateCapital("Maharashtra", "Mumbai");
        addStateCapital("Tamil Nadu", "Chennai");
        addStateCapital("Gujarat", "Gandhinagar");
        addStateCapital("West Bengal", "Kolkata");
        addStateCapital("Rajasthan", "Jaipur");
        addStateCapital("Uttar Pradesh", "Lucknow");

        System.out.println("Welcome to the State-Capital Quiz!");

        System.out.print("Enter the number of questions you want in the quiz: ");
        int numQuestions = scanner.nextInt();
        scanner.nextLine();  

        conductQuiz(numQuestions);
    }
}

