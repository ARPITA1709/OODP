class Vehicle {
public:
    int speed;
    float fuelLevel;

    void displayStatus() {
        std::cout << "Speed: " << speed << " km/h, Fuel Level: " << fuelLevel << " liters\n";
    }
};

// Pointer to data member 'speed'
int Vehicle::*ptrSpeed; 

// Pointer to member function 'displayStatus'
void (Vehicle::*ptrDisplayStatus)();


(b) Code Snippet Using Pointers to Class Members

#include <iostream>

class Vehicle {
public:
    int speed;
    float fuelLevel;

    Vehicle(int spd, float fuel) : speed(spd), fuelLevel(fuel) {}

    void displayStatus() {
        std::cout << "Speed: " << speed << " km/h, Fuel Level: " << fuelLevel << " liters\n";
    }
};

int main() {
    Vehicle car(0, 50.0f); // Create a Vehicle object with initial values

    // Pointer to data member 'speed'
    int Vehicle::*ptrSpeed = &Vehicle::speed;

    // Pointer to member function 'displayStatus'
    void (Vehicle::*ptrDisplayStatus)() = &Vehicle::displayStatus;

    // Modifying speed using pointer to member
    car.*ptrSpeed = 100;  // Accessing the member using object

    // Calling displayStatus using pointer to member function
    (car.*ptrDisplayStatus)();

    return 0;
}

