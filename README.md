#include <iostream>

class Vehicle {
public:
    int speed;
    float fuelLevel;

    Vehicle() : speed(0), fuelLevel(100.0f) {}

    // Member function to display the vehicle's status
    void displayStatus() {
        std::cout << "Speed: " << speed << " km/h, Fuel Level: " << fuelLevel << "%" << std::endl;
    }
};

int main() {
    // Create a Vehicle object
    Vehicle myCar;

    // Pointer to data member 'speed'
    int Vehicle::*ptrToSpeed = &Vehicle::speed;

    // Pointer to member function 'displayStatus'
    void (Vehicle::*ptrToDisplayStatus)() = &Vehicle::displayStatus;

    // Use the pointer to set the speed
    myCar.*ptrToSpeed = 120;  // Set speed to 120 km/h

    // Use the pointer to call the displayStatus function
    (myCar.*ptrToDisplayStatus)();  // Output the status of the vehicle

    return 0;
}

