import java.util.ArrayList;
import java.util.Scanner;

public class WeeklyTemp {
    public static void main(String[] args) {
        ArrayList<String> daysOfWeek = new ArrayList<>();
        ArrayList<Double> temperatures = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);

        // Collect data for each day of the week
        for (int i = 0; i < 7; i++) {
            System.out.print("Enter the day of the week: ");
            String day = scanner.nextLine();
            System.out.print("Enter the average temperature for " + day + ": ");
            double temperature = scanner.nextDouble();

            daysOfWeek.add(day);
            temperatures.add(temperature);

            scanner.nextLine(); 
        }

        while (true) {
            System.out.print("Enter a day of the week (Monday to Sunday) or 'week' for weekly average (or 'exit' to quit): ");
            String input = scanner.nextLine();

            if (input.equalsIgnoreCase("exit")) {
                break;
            }

            if (input.equalsIgnoreCase("week")) {
                double weeklyAverage = calculateWeeklyAverage(temperatures);
                System.out.println("Weekly average temperature: " + weeklyAverage);
            } else {
                int index = daysOfWeek.indexOf(input);
                if (index >= 0) {
                    String day = daysOfWeek.get(index);
                    double temperature = temperatures.get(index);
                    System.out.println(day + ": " + temperature + " degrees");
                } else {
                    System.out.println("Invalid input. Please enter a valid day or 'week'.");
                }
            }
        }

        scanner.close();
    }

    private static double calculateWeeklyAverage(ArrayList<Double> temperatures) {
        double sum = 0;
        for (double temperature : temperatures) {
            sum += temperature;
        }
        return sum / temperatures.size();
    }
}
