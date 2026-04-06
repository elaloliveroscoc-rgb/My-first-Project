import java.util.ArrayList;
import java.util.Scanner;
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

class Report {
    int id;
    String location;
    String problem;
    String status;
    String dateReported;
    String scheduleDate;

    Report(int id, String location, String problem) {
        this.id = id;
        this.location = location;
        this.problem = problem;
        this.status = "P";

        DateTimeFormatter format = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm");
        this.dateReported = LocalDateTime.now().format(format);

        this.scheduleDate = "Not yet scheduled";
    }
}

public class Main {
    static ArrayList<Report> reports = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);
    static int counter = 1;

    public static void main(String[] args) {
        while (true) {
            System.out.println("\n=== MAIN MENU ===");
            System.out.println("1. Admin");
            System.out.println("2. Resident");
            System.out.println("3. Exit");
            System.out.print("Choice: ");

            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    adminMenu();
                    break;
                case 2:
                    residentMenu();
                    break;
                case 3:
                    System.out.println("END");
                    return;
                default:
                    System.out.println("Invalid Input! Try again.");
            }
        }
    }

    static void adminMenu() {
        while (true) {
            System.out.println("\n=== ADMIN MENU ===");
            System.out.println("1. View Reports & Schedule");
            System.out.println("2. Update Report (Set Schedule / Resolve)");
            System.out.println("3. Exit");
            System.out.print("Choice: ");

            int choice = sc.nextInt();
            sc.nextLine();

            if (choice == 1) {
                viewReports();
            } else if (choice == 2) {
                updateReport();
            } else if (choice == 3) {
                return;
            } else {
                System.out.println("Invalid Input!");
            }
        }
    }

    static void residentMenu() {
        while (true) {
            System.out.println("\n=== RESIDENT MENU ===");
            System.out.println("1. Report a Problem");
            System.out.println("2. View Schedule");
            System.out.println("3. Exit");
            System.out.print("Choice: ");

            int choice = sc.nextInt();
            sc.nextLine();

            if (choice == 1) {
                reportProblem();
            } else if (choice == 2) {
                viewReports();
            } else if (choice == 3) {
                return;
            } else {
                System.out.println("Invalid Choice! Try again.");
            }
        }
    }

    static void reportProblem() {
        System.out.print("Enter Location: ");
        String location = sc.nextLine();

        System.out.print("Enter Problem: ");
        String problem = sc.nextLine();

        reports.add(new Report(counter++, location, problem));
        System.out.println("Problem Successfully Reported!");
    }

    static void viewReports() {
        if (reports.isEmpty()) {
            System.out.println("No reports available.");
            return;
        }

        System.out.println("\n=== REPORT & SCHEDULE ===");

        for (Report r : reports) {
            String statusText = r.status.equals("P") ? "Pending" : "Resolved";

            System.out.println("ID: " + r.id +
                    "\nLocation: " + r.location +
                    "\nProblem: " + r.problem +
                    "\nReported On: " + r.dateReported +
                    "\nScheduled On: " + r.scheduleDate +
                    "\nStatus: " + statusText +
                    "\n---------------------------");
        }
    }

    static void updateReport() {
        if (reports.isEmpty()) {
            System.out.println("No reports to update.");
            return;
        }

        System.out.print("Enter Report ID: ");
        int id = sc.nextInt();
        sc.nextLine();

        for (Report r : reports) {
            if (r.id == id) {

                System.out.print("Enter Schedule Date (YYYY-MM-DD HH:MM): ");
                r.scheduleDate = sc.nextLine();

                System.out.print("Mark as Resolved? (y/n): ");
                char choice = sc.next().charAt(0);

                if (choice == 'y' || choice == 'Y') {
                    r.status = "R";
                }

                System.out.println("Report updated successfully!");
                return;
            }
        }

        System.out.println("Invalid ID!");
    }
}
