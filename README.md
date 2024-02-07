import java.util.*;
import java.time.*;
import javax.lang.model.SourceVersion;

class BloodSugar {
    private int id;
    private String name;
    private int yob;
    private int sugarLevel;

    public BloodSugar(int id, String name, int yob, int sugarLevel) {
        this.id = id;
        this.name = name;
        this.yob = yob;
        this.sugarLevel = sugarLevel;
    }

    // Setters and Getters
    // ...

    public void display() {
        System.out.println("ID: " + id + ", Name: " + name + ", Age: " + calculateAge() + ", Sugar Level: " + sugarLevel);
    }

    private int calculateAge() {
        int currentYear = Year.now().getValue();
        return currentYear - yob;
    }

    @Override
    public SourceVersion getSupportedSourceVersion() {
        return SourceVersion.latest();
    }
}

public class BloodSugar{
    private List<BloodSugar> records;

    public Tester() {
        records = new ArrayList<>();
    }

    public void displayMenu() {
        System.out.println("1. Create a record");
        System.out.println("2. Show blood sugar data for all users");
        System.out.println("3. Show blood sugar data for a selected user");
        System.out.println("4. Delete all");
        System.out.println("5. Exit application");
    }

    public void index() {
        for (BloodSugar record : records) {
            record.display();
        }
    }

    public void view(int id) {
        for (BloodSugar record : records) {
            if (record.getId() != id) {
            } else {
                record.display();
                // Add blood sugar category and recommendations here
                break;
            }
        }
    }

    public void create(int id, String name, int yob, int sugarLevel) {
        BloodSugar newRecord = new BloodSugar(id, name, yob, sugarLevel);
        records.add(newRecord);
    }

    public void delete() {
        records.clear();
    }

    public void exit() {
        System.exit(0);
    }

    public static void main(String[] args) {
        Tester tester = new Tester();
        Scanner scanner = new Scanner(System.in);
        String choice;

        do {
            tester.displayMenu();
            System.out.print("Enter your choice: ");
            choice = scanner.nextLine();

            switch (choice) {
                case "1":
                    // Gather input for new record and call create method
                    break;
                case "2":
                    tester.index();
                    break;
                case "3":
                    System.out.print("Enter user ID: ");
                    int id = scanner.nextInt();
                    tester.view(id);
                    break;
                case "4":
                    tester.delete();
                    break;
                case "5":
                    tester.exit();
                    break;
                default:
                    System.out.println("Invalid choice");
            }
        } while (!choice.equals("5"));
    }
}
