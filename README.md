#include <iostream>
#include <vector>
#include <string>

class Book {
public:
    std::string title;
    std::string author;
    std::string isbn;
    bool available;

    // Constructor
    Book(std::string t, std::string a, std::string i)
        : title(t), author(a), isbn(i), available(true) {}

    // Display book details
    void displayBook() const {
        std::cout << "Title: " << title << "\nAuthor: " << author 
                  << "\nISBN: " << isbn << "\nStatus: " 
                  << (available ? "Available" : "Not Available") << "\n\n";
    }
};

class Library {
private:
    std::vector<Book> books;

public:
    // Add a new book to the library
    void addBook(const Book& book) {
        books.push_back(book);
        std::cout << "Book added: " << book.title << "\n";
    }

    // Search for a book by title
    void searchBookByTitle(const std::string& title) const {
        for (const auto& book : books) {
            if (book.title == title) {
                std::cout << "Book found:\n";
                book.displayBook();
                return;
            }
        }
        std::cout << "Book not found.\n";
    }

    // Borrow a book by ISBN
    void borrowBook(const std::string& isbn) {
        for (auto& book : books) {
            if (book.isbn == isbn) {
                if (book.available) {
                    book.available = false;
                    std::cout << "Book borrowed successfully: " << book.title << "\n";
                } else {
                    std::cout << "Book is already borrowed.\n";
                }
                return;
            }
        }
        std::cout << "Book not found.\n";
    }

    // Return a book by ISBN
    void returnBook(const std::string& isbn) {
        for (auto& book : books) {
            if (book.isbn == isbn) {
                if (!book.available) {
                    book.available = true;
                    std::cout << "Book returned successfully: " << book.title << "\n";
                } else {
                    std::cout << "Book was not borrowed.\n";
                }
                return;
            }
        }
        std::cout << "Book not found.\n";
    }

    // Display all books in the library
    void displayAllBooks() const {
        if (books.empty()) {
            std::cout << "No books in the library.\n";
            return;
        }
        std::cout << "Library Books:\n";
        for (const auto& book : books) {
            book.displayBook();
        }
    }
};

int main() {
    Library library;
    
    // Adding books to the library
    library.addBook(Book("C++ Programming", "Bjarne Stroustrup", "123456789"));
    library.addBook(Book("Introduction to Algorithms", "Cormen", "987654321"));
    
    // Searching for a book
    library.searchBookByTitle("C++ Programming");

    // Borrowing a book
    library.borrowBook("123456789");

    // Trying to borrow an already borrowed book
    library.borrowBook("123456789");

    // Returning the book
    library.returnBook("123456789");

    // Display all books
    library.displayAllBooks();

    return 0;
}
