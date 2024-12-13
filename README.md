public class Account {
    private String accountNumber;
    private String pin;
    private double balance;

   Constructor, getters, and setters

 public void deposit(double amount) {
        balance += amount;
    }

public void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
        } else {
            System.out.println("Insufficient funds!");
        }
    }

 public void displayBalance() {
        System.out.println("Your balance is: " + balance);
    }
}
import java.util.Scanner;

public class ATMInterface {
    private static Scanner scanner = new Scanner(System.in);

   public static void main(String[] args) {
        Account userAccount = new Account("12345", "1234", 1000.0); // Example account
        ATMInterface atm = new ATMInterface();
        atm.showMenu(userAccount);
    }

  public void showMenu(Account account) {
        while (true) {
            System.out.println("ATM Menu:");
            System.out.println("1. Check Balance");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Change PIN");
            System.out.println("5. Exit");

  System.out.print("Select an option: ");
            int choice = scanner.nextInt();

 switch (choice) {
                case 1:
                    account.displayBalance();
                    break;
                case 2:
                    System.out.print("Enter deposit amount: ");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;
                case 3:
                    System.out.print("Enter withdrawal amount: ");
                    double withdrawAmount = scanner.nextDouble();
                    account.withdraw(withdrawAmount);
                    break;
                case 4:
                    System.out.print("Enter new PIN: ");
                    String newPin = scanner.next();
                    account.setPin(newPin);
                    System.out.println("PIN changed successfully!");
                    break;
                case 5:
                    System.out.println("Thank you for using the ATM!");
                    return;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }
}
