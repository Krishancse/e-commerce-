# e-commerce-
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Requirement {
    private int id;
    private String description;
    private String status;

    public Requirement(int id, String description) {
        this.id = id;
        this.description = description;
        this.status = "Pending";
    }

    public void setStatus(String status) {
        this.status = status;
    }

    @Override
    public String toString() {
        return "Requirement " + id + ": " + description + " (" + status + ")";
    }
}

public class RequirementManagementApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        List<Requirement> requirements = new ArrayList<>();

        int requirementId = 1;
        boolean running = true;

        System.out.println("Requirement Management Application");
        
        while (running) {
            System.out.println("1. Add Requirement");
            System.out.println("2. View Requirements");
            System.out.println("3. Update Requirement Status");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline
            
            switch (choice) {
                case 1:
                    System.out.print("Enter requirement description: ");
                    String description = scanner.nextLine();
                    requirements.add(new Requirement(requirementId++, description));
                    System.out.println("Requirement added successfully.");
                    break;
                case 2:
                    System.out.println("Requirements:");
                    for (Requirement requirement : requirements) {
                        System.out.println(requirement);
                    }
                    break;
                case 3:
                    System.out.print("Enter requirement ID to update status: ");
                    int idToUpdate = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    
                    for (Requirement requirement : requirements) {
                        if (requirement.id == idToUpdate) {
                            System.out.print("Enter new status (Pending, In Progress, Completed): ");
                            String newStatus = scanner.nextLine();
                            requirement.setStatus(newStatus);
                            System.out.println("Status updated successfully.");
                            break;
                        }
                    }
                    break;
                case 4:
                    running = false;
                    System.out.println("Exiting Requirement Management Application.");
                    break;
                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        }

        scanner.close();
    }
}
