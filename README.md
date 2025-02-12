#include <iostream>
#include <string>

class BankAccount {
private:
    int accountNumber;
    double balance;
    std::string accountHolderName;

public:
    // Constructor
    BankAccount(int accNumber, double initialBalance, const std::string& holderName)
        : accountNumber(accNumber), balance(initialBalance), accountHolderName(holderName) {}

    // Deposit method
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            std::cout << "Deposit successful! New balance: $" << balance << std::endl;
        } else {
            std::cout << "Invalid deposit amount!" << std::endl;
        }
    }

    // Withdraw method
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            std::cout << "Withdrawal successful! New balance: $" << balance << std::endl;
        } else if (amount > balance) {
            std::cout << "Insufficient funds! Withdrawal denied." << std::endl;
        } else {
            std::cout << "Invalid withdrawal amount!" << std::endl;
        }
    }

    // Display balance
    void displayBalance() const {
        std::cout << "Account Balance: $" << balance << std::endl;
    }
};

int main() {
    int accNumber;
    double initialBalance;
    std::string holderName;

    // Get account details from the user
    std::cout << "Enter account number: ";
    std::cin >> accNumber;
    std::cin.ignore();  // Ignore newline character left in buffer

    std::cout << "Enter account holder name: ";
    std::getline(std::cin, holderName);

    std::cout << "Enter initial balance: ";
    std::cin >> initialBalance;

    // Create BankAccount object
    BankAccount account(accNumber, initialBalance, holderName);

    int choice;
    do {
        std::cout << "\n1. Deposit\n2. Withdraw\n3. Display Balance\n4. Exit\n";
        std::cout << "Choose an option: ";
        std::cin >> choice;

        if (choice == 1) {
            double amount;
            std::cout << "Enter deposit amount: ";
            std::cin >> amount;
            account.deposit(amount);
        } else if (choice == 2) {
            double amount;
            std::cout << "Enter withdrawal amount: ";
            std::cin >> amount;
            account.withdraw(amount);
        } else if (choice == 3) {
            account.displayBalance();
        } else if (choice == 4) {
            std::cout << "Exiting program. Thank you!\n";
        } else {
            std::cout << "Invalid choice! Please try again.\n";
        }
    } while (choice != 4);

    return 0;
}
