#include <iostream>
#include <string>

class Student {
public:
    std::string name;  // Public member (can be accessed and modified directly)

    // Constructor to initialize Student object
    Student(const std::string& studentName, int studentId) 
        : name(studentName), id(studentId) {}

    // Getter function to access the private 'id' member
    int getId() const {
        return id;
    }

private:
    int id;  // Private member, only accessible via getId()
};

int main() {
    // Creating a Student object
    Student student("Alice", 12345);

    // Directly accessing and modifying the public 'name' member
    student.name = "Bob";  

    // Accessing the private 'id' member using the getter function
    std::cout << "Student Name: " << student.name << std::endl;
    std::cout << "Student ID: " << student.getId() << std::endl;

    return 0;
}
