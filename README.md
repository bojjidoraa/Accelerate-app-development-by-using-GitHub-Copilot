# Library App

## Description

Library App is a .NET 8 console application designed to manage library operations. It provides functionality for patrons to search their profiles, view book loans, renew memberships, extend loan periods, and return books. The application uses a JSON-based data storage system and follows clean architecture principles with separation of concerns across multiple layers.

## Project Structure

- `src/`
  - `Library.ApplicationCore/` - Core business logic and domain entities
    - `Entities/` - Domain models (Author, Book, BookItem, Loan, Patron)
    - `Enums/` - Enumeration types for status results (LoanExtensionStatus, LoanReturnStatus, MembershipRenewalStatus)
    - `Interfaces/` - Abstractions for repositories and services (IPatronRepository, ILoanRepository, IPatronService, ILoanService)
    - `Services/` - Business logic services (PatronService, LoanService)
  - `Library.Console/` - Console application UI layer
    - `Json/` - JSON data files (Authors.json, Books.json, BookItems.json, Loans.json, Patrons.json)
    - `ConsoleApp.cs` - Main application logic and user interaction
    - `ConsoleState.cs` - State management enum for the console application
    - `CommonActions.cs` - Common user action flags
    - `appSettings.json` - Application configuration
  - `Library.Infrastructure/` - Data access and infrastructure layer
    - `Data/` - Repository implementations (JsonPatronRepository, JsonLoanRepository, JsonData)
- `tests/`
  - `UnitTests/` - Unit test project
    - `ApplicationCore/` - Tests for services
      - `PatronService/` - Tests for patron membership renewal
      - `LoanService/` - Tests for loan operations
    - `PatronFactory.cs` - Factory for creating test patron objects
    - `LoanFactory.cs` - Factory for creating test loan objects

## Key Classes and Interfaces

**Entities:**
- [`Patron`](src/Library.ApplicationCore/Entities/Patron.cs) - Represents a library patron with membership information
- [`Loan`](src/Library.ApplicationCore/Entities/Loan.cs) - Represents a book loan transaction
- [`Book`](src/Library.ApplicationCore/Entities/Book.cs) - Represents a book in the library
- [`BookItem`](src/Library.ApplicationCore/Entities/BookItem.cs) - Represents a physical copy of a book
- [`Author`](src/Library.ApplicationCore/Entities/Author.cs) - Represents a book author

**Services:**
- [`IPatronService`](src/Library.ApplicationCore/Interfaces/IPatronService.cs) / [`PatronService`](src/Library.ApplicationCore/Services/PatronService.cs) - Handles patron membership renewal logic
- [`ILoanService`](src/Library.ApplicationCore/Interfaces/ILoanService.cs) / [`LoanService`](src/Library.ApplicationCore/Services/LoanService.cs) - Handles loan operations (return, extend)

**Repositories:**
- [`IPatronRepository`](src/Library.ApplicationCore/Interfaces/IPatronRepository.cs) / [`JsonPatronRepository`](src/Library.Infrastructure/Data/JsonPatronRepository.cs) - Patron data access
- [`ILoanRepository`](src/Library.ApplicationCore/Interfaces/ILoanRepository.cs) / [`JsonLoanRepository`](src/Library.Infrastructure/Data/JsonLoanRepository.cs) - Loan data access
- [`JsonData`](src/Library.Infrastructure/Data/JsonData.cs) - Central data management for JSON file operations

**UI:**
- [`ConsoleApp`](src/Library.Console/ConsoleApp.cs) - Main console application controller

## Usage

1. **Build the project:**

2. **Run the console application:**
3. **Run unit tests:**
### Console Application Features

- **Search Patrons** - Search for library patrons by name
- **View Patron Details** - Display patron information and active loans
- **Renew Membership** - Extend a patron's membership expiration date (available within 1 month before expiration and with no overdue loans)
- **View Loan Details** - Display detailed information about a specific book loan
- **Return Book** - Mark a loaned book as returned
- **Extend Loan** - Extend the due date of an active loan by 14 days (requires active membership)

## License

This project is provided as-is for educational purposes.