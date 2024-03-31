import java.util.ArrayList;
import java.util.Calendar;
import java.util.Scanner;

class BloodSugar {
    private String name;
    private int yearOfBirth;
    private double bloodSugarLevel;

    public BloodSugar(String name, int yearOfBirth, double bloodSugarLevel) {
        this.name = name;
        this.yearOfBirth = yearOfBirth;
        this.bloodSugarLevel = bloodSugarLevel;
    }

    public void display() {
        System.out.println("Name: " + name);
        System.out.println("Year of Birth: " + yearOfBirth);
        System.out.println("Blood Sugar Level: " + bloodSugarLevel);
    }

    public String getCategory() {
        // Logic to determine blood sugar category
        return "Normal"; // Placeholder
    }

    public String getRecommendation() {
        // Logic to provide recommendations based on blood sugar level
        return "No recommendations"; // Placeholder
    }

    // Calculate age based on the current year
    public int calculateAge() {
        Calendar now = Calendar.getInstance();
        int currentYear = now.get(Calendar.YEAR);
        return currentYear - yearOfBirth;
    }

    // Getters and setters...
}

public class BloodSugarMonitor {
    private ArrayList<BloodSugar> users;

    public BloodSugarMonitor() {
        this.users = new ArrayList<>();
    }

    public void index() {
        for (BloodSugar user : users) {
            user.display();
        }
    }

    public void view(int id) {
        if (id >= 0 && id < users.size()) {
            BloodSugar user = users.get(id);
            user.display();
            System.out.println("Age: " + user.calculateAge());
            System.out.println("Category: " + user.getCategory());
            System.out.println("Recommendation: " + user.getRecommendation());
        } else {
            System.out.println("Invalid user ID");
        }
    }

    public void create() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter name:");
        String name = scanner.nextLine();
        System.out.println("Enter year of birth:");
        int yearOfBirth = scanner.nextInt();
        System.out.println("Enter blood sugar level:");
        double bloodSugarLevel = scanner.nextDouble();
        BloodSugar user = new BloodSugar(name, yearOfBirth, bloodSugarLevel);
        users.add(user);
    }

    public void delete() {
        users.clear();
        System.out.println("All records deleted.");
    }

    public void exit() {
        System.out.println("Exiting...");
        System.exit(0);
    }

    public static void main(String[] args) {
        BloodSugarMonitor monitor = new BloodSugarMonitor();
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("Menu:");
            System.out.println("1. Create a record");
            System.out.println("2. Show blood sugar data for all users");
            System.out.println("3. Show blood sugar data for a selected user");
            System.out.println("4. Delete all");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            switch (choice) {
                case 1:
                    monitor.create();
                    break;
                case 2:
                    monitor.index();
                    break;
                case 3:
                    System.out.print("Enter user ID: ");
                    int id = scanner.nextInt();
                    monitor.view(id);
                    break;
                case 4:
                    monitor.delete();
                    break;
                case 5:
                    monitor.exit();
                    break;
                default:
                    System.out.println("Invalid choice");
            }
        }
    }
}

      

  
    
