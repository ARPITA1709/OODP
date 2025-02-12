#include <iostream>

class Vehicle {
public:
    int speed;        // Speed of the vehicle
    float fuelLevel;  // Fuel level in percentage

    // Constructor to initialize the vehicle attributes
    Vehicle(int spd, float fuel) : speed(spd), fuelLevel(fuel) {}

    // Function to display the current status of the vehicle
    void displayStatus() const {
        std::cout << "Speed: " << speed << " km/h, Fuel Level: " << fuelLevel << "%\n";
    }
};

int main() {
    // Create a Vehicle object
    Vehicle car(80, 50.5);

    // Pointer to data members
    int Vehicle::*speedPtr = &Vehicle::speed;       // Pointer to speed member
    float Vehicle::*fuelPtr = &Vehicle::fuelLevel;  // Pointer to fuelLevel member

    // Access and modify members using pointers
    std::cout << "Initial Vehicle Status:\n";
    car.displayStatus();

    // Modify using pointers
    car.*speedPtr = 100;   // Update speed using pointer
    car.*fuelPtr = 40.0;   // Update fuelLevel using pointer

    std::cout << "\nUpdated Vehicle Status:\n";
    car.displayStatus();

    // Pointer to member function
    void (Vehicle::*displayPtr)() const = &Vehicle::displayStatus;

    std::cout << "\nDisplaying status using a pointer to member function:\n";
    (car.*displayPtr)();  // Call function using pointer

    return 0;
}
