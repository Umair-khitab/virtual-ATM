#import java.util.Scanner;

// Class to represent a bank account
class Account {
    private String accountHolder;
    private int accountNumber;
    private double balance;

    public Account(String accountHolder, int accountNumber, double initialBalance) {
        this.accountHolder = accountHolder;
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
    }

    public String getAccountHolder() {
        return accountHolder;
    }

    public int getAccountNumber() {
        return accountNumber;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposit successful! Your new balance is: $" + balance);
        } else {
            System.out.println("Please enter a valid deposit amount.");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawal successful! Your new balance is: $" + balance);
        } else {
            System.out.println("Insufficient balance or invalid withdrawal amount.");
        }
    }
}

// Class to simulate ATM operations
class ATM {
    private Account account;

    public ATM(Account account) {
        this.account = account;
    }

    public void showMenu() {
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\nWelcome, " + account.getAccountHolder() + "!");
            System.out.println("1. Check Balance");
            System.out.println("2. Deposit Money");
            System.out.println("3. Withdraw Money");
            System.out.println("4. Exit");
            System.out.print("Please select an option: ");

            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Your current balance is: $" + account.getBalance());
                    break;
                case 2:
                    System.out.print("Enter the amount to deposit: ");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;
                case 3:
                    System.out.print("Enter the amount to withdraw: ");
                    double withdrawAmount = scanner.nextDouble();
                    account.withdraw(withdrawAmount);
                    break;
                case 4:
                    System.out.println("Thank you for using our ATM. Have a great day!");
                    break;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        } while (choice != 4);

        scanner.close();
    }
}

// Main class to run the ATM system
public class ATMSystem {
    public static void main(String[] args) {
        // Create a sample account
        Account account = new Account("umair khitab", 123456, 1000.0);

        // Set up the ATM with the account
        ATM atm = new ATM(account);

        // Start the ATM menu
        atm.showMenu();
    }
}
