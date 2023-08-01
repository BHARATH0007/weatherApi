# weatherApi
import java.io.IOException;
import java.util.Scanner;

public class WeatherApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            displayMenu();

            int option = scanner.nextInt();
            scanner.nextLine(); // Consume the newline character after reading the integer

            switch (option) {
                case 1:
                    getAndPrintWeatherData(scanner);
                    break;
                case 2:
                    getAndPrintWindSpeedData(scanner);
                    break;
                case 3:
                    getAndPrintPressureData(scanner);
                    break;
                case 0:
                    System.out.println("Exiting the program. Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }

    private static void displayMenu() {
        System.out.println("Menu:");
        System.out.println("1. Get weather");
        System.out.println("2. Get Wind Speed");
        System.out.println("3. Get Pressure");
        System.out.println("0. Exit");
        System.out.print("Enter your choice: ");
    }

    private static void getAndPrintWeatherData(Scanner scanner) {
        System.out.print("Enter the date: ");
        String date = scanner.nextLine();
        try {
            String response = WeatherAPI.getHourlyWeatherForecast(date);
            // Parse the JSON response and extract temperature data
            // You can use a JSON library like Jackson or Gson for parsing.
            // For simplicity, let's assume the response is in a specific format.
            double temperature = 0.0; // Replace with actual parsed temperature value
            System.out.println("Temperature on " + date + ": " + temperature + " °C");
        } catch (IOException e) {
            System.out.println("Error fetching data from the API. Please try again.");
        }
    }

    private static void getAndPrintWindSpeedData(Scanner scanner) {
        // Similar to getAndPrintWeatherData but for wind.speed
        // Implement based on your API response format.
    }

    private static void getAndPrintPressureData(Scanner scanner) {
        // Similar to getAndPrintWeatherData but for pressure
        // Implement based on your API response format.
    }
}
