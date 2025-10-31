# Library-Management-System-in-C-


Algorithm with pseudo code.


// 1. Book Class Definition
class Book {
private:
    int bookID;
    std::string title;
    std::string author;
    bool isIssued;

public:
    // Constructor (to be expanded for initialization)
    Book() : bookID(0), isIssued(false) {}

    void addBook() {
        std::cout << "Enter Book ID: ";
        std::cin >> bookID;
        std::cin.ignore(); // Consume newline
        std::cout << "Enter Title: ";
        std::getline(std::cin, title);
        std::cout << "Enter Author: ";
        std::getline(std::cin, author);
        isIssued = false;
    }

    void showBook() const {
        std::cout << "\nID: " << bookID
                  << "\nTitle: " << title
                  << "\nAuthor: " << author
                  << "\nStatus: " << (isIssued ? "Issued" : "Available")
                  << std::endl;
    }

    // Getters
    int getID() const { return bookID; }
    bool getStatus() const { return isIssued; }
    void setStatus(bool status) { isIssued = status; }
};

// 2. Library Class Definition
class Library {
private:
    std::vector<Book> books;

public:
    void addBookToCollection() {
        Book newBook;
        newBook.addBook();
        books.push_back(newBook);
        std::cout << "\nBook added successfully!" << std::endl;
    }

    void displayAllBooks() const {
        if (books.empty()) {
            std::cout << "\nThe library is empty." << std::endl;
            return;
        }
        for (const auto& book : books) {
            book.showBook();
        }
    }

    // ... (Issue, Return, Search functions would be defined here) ...
};

// 3. Main function (User Interface)
int main() {
    Library lib;
    int choice;

    do {
        std::cout << "\n\n=== Library Management System ==="
                  << "\n1. Add Book"
                  << "\n2. Display All Books"
                  << "\n3. Exit"
                  << "\nEnter your choice: ";
        std::cin >> choice;

        switch (choice) {
            case 1:
                lib.addBookToCollection();
                break;
            case 2:
                lib.displayAllBooks();
                break;
            case 3:
                std::cout << "Exiting system. Goodbye!" << std::endl;
                break;
            default:
                std::cout << "Invalid choice. Please try again." << std::endl;
        }
    } while (choice != 3);

    return 0;
}
