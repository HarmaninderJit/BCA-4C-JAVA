Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 

Implement the following queries:

a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.

b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.

c) Count the total number of Employees whose GrossSalary is less than 35000/-



package assign1;
import java.util.Scanner;

public class Employee {
	private String nameOfEmp;
    private int empId;
    private double basicSalary;
    private double grossSalary;

    // Constructor
    public Employee(String nameOfEmp, int empId, double basicSalary) {
        this.nameOfEmp = nameOfEmp;
        this.empId = empId;
        this.basicSalary = basicSalary;
        calculateGrossSalary();
    }

    // Method to calculate GrossSalary
    private void calculateGrossSalary() {
        double hra = 0.25 * basicSalary;
        double da = 0.40 * basicSalary;
        grossSalary = basicSalary + hra + da;
    }

    // Getter methods
    public String getNameOfEmp() {
        return nameOfEmp;
    }

    public int getEmpId() {
        return empId;
    }

    public double getGrossSalary() {
        return grossSalary;
    }

    // Method to check if the name starts with a consonant
    public boolean startsWithConsonant() {
        char firstChar = nameOfEmp.toLowerCase().charAt(0);
        return !(firstChar == 'a' || firstChar == 'e' || firstChar == 'i' || firstChar == 'o' || firstChar == 'u');
    }

    // Method to check if the empId is between 101 and 150
    public boolean isEmpIdInRange() {
        return empId >= 101 && empId <= 150;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Taking input from user
        System.out.print("Enter the number of employees: ");
        int numEmployees = scanner.nextInt();
        scanner.nextLine(); // Consume newline

        Employee[] employees = new Employee[numEmployees];

        // Input employee details
        for (int i = 0; i < numEmployees; i++) {
            System.out.println("\nEnter details for Employee " + (i + 1) + ":");
            System.out.print("Name: ");
            String name = scanner.nextLine();
            System.out.print("Emp ID: ");
            int empId = scanner.nextInt();
            System.out.print("Basic Salary: ");
            double basicSalary = scanner.nextDouble();
            scanner.nextLine(); // Consume newline

            employees[i] = new Employee(name, empId, basicSalary);
        }

        // Query a) Display the NameOfEmp and GrossSalary of employees whose name starts with a consonant.
        System.out.println("\nEmployees whose name starts with a consonant:");
        for (Employee emp : employees) {
            if (emp.startsWithConsonant()) {
                System.out.println("Name: " + emp.getNameOfEmp() + ", Gross Salary: " + emp.getGrossSalary());
            }
        }

        // Query b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
        System.out.println("\nEmployees whose Emp-Id is between 101 and 150:");
        for (Employee emp : employees) {
            if (emp.isEmpIdInRange()) {
                System.out.println("Emp ID: " + emp.getEmpId() + ", Gross Salary: " + emp.getGrossSalary());
            }
        }

        // Query c) Count the total number of Employees whose GrossSalary is less than 35000/-
        int count = 0;
        for (Employee emp : employees) {
            if (emp.getGrossSalary() < 35000) {
                count++;
            }
        }
        System.out.println("\nTotal number of employees with Gross Salary less than 35000: " + count);
    }
}



