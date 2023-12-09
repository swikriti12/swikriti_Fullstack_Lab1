# swikriti_Fullstack_Lab1

import java.util.Random;

class Employee {
    String firstName;
    String lastName;

    // Parameterized constructor
    public Employee(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
}

class CredentialService {
    Employee employee;
    String department;

    // Parameterized constructor
    public CredentialService(Employee employee, String department) {
        this.employee = employee;
        this.department = department;
    }

    public String generateEmailAddress() {
        return employee.firstName.toLowerCase() + employee.lastName.toLowerCase() +
                "@" + department.toLowerCase() + ".company.com";
    }

    public String generatePassword() {
        String characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()-_=+";
        StringBuilder password = new StringBuilder();
        Random random = new Random();

        for (int i = 0; i < 8; i++) {
            password.append(characters.charAt(random.nextInt(characters.length())));
        }

        return password.toString();
    }

    public void showCredentials() {
        String email = generateEmailAddress();
        String password = generatePassword();

        System.out.println("Dear " + employee.firstName + ", your generated credentials are as follows:");
        System.out.println("Email ---> " + email);
        System.out.println("Password ---> " + password);
    }
}

public class Main {
    public static void main(String[] args) {
        // Example usage
        Employee newEmployee = new Employee("Harshit", "Choudary");
        String department = "Tech";

        CredentialService credentialService = new CredentialService(newEmployee, department);
        credentialService.showCredentials();
    }
}
