# Personal Library Management System

A Java Swing desktop application for managing a personal collection of books, tracking reading progress, ratings, and statistics. 

> **Academic Note:** This project was developed as part of the **3rd Year Software Engineering Course** for the **Bachelor’s Degree in Computer Engineering**.

---

## 📌 Project Overview

The **Personal Library Manager** is designed to demonstrate clean software architecture, object-oriented design principles, and classical software design patterns in Java. It provides an intuitive Graphical User Interface (GUI) built with Java Swing to allow users to organize, search, filter, and track their personal book collection.

---

## ✨ Features

- **Book Management:** Add, update, delete, and view detailed information for books (Title, Author, Genre, ISBN, Publication Year, Reading Status, Rating).
- **Advanced Filtering & Search:** Filter books dynamically by genre, reading status (`TO_READ`, `READING`, `COMPLETED`), title/author search, or combined criteria.
- **Persistence:** Save and load book collections in JSON or XML format using Jackson libraries.
- **Library Statistics:** Overview panel displaying statistics such as total books, books read, average ratings, and breakdown by genre.
- **Input Validation & Capacity Limits:** Robust validation checks ensuring data integrity and enforcing capacity constraints.
- **Unit Testing:** Comprehensive test suite built with JUnit covering core controllers, filtering logic, validation rules, and persistence operations.

---

## 🛠️ Architecture & Design Patterns

The system adheres to strict software design patterns to ensure scalability, maintainability, and loose coupling:

1. **Model-View-Controller (MVC):**
   - **Model (`model`):** Encapsulates core business domain, book structures, enums (`StatoLettura`, `Valutazione`), and filtering logic.
   - **View (`view`):** Swing components (`MainFrame`, `BookTablePanel`, `BookFormPanel`, `SearchPanel`, `StatisticheLibreriaPanel`, and dialogs).
   - **Controller (`controller`):** Coordinates data flow between View and Model (`LibreriaController`, `BookManagerController`).

2. **Observer Pattern (`model.observer`):**
   - `LibreriaSubject` and `LibreriaObserver` enable reactive UI updates whenever books are added, modified, or removed.

3. **Factory Pattern (`model.accesslogic`):**
   - `LibroFactory`, `JSONLibroFactory`, and `XMLLibroFactory` abstract the creation and handling of book representations across formats.

4. **Strategy & Command Patterns (`model.strategy` / `model.command`):**
   - Encapsulates search and filtering strategies (`FiltroGenereStrategy`, `FiltroStatoLetturaStrategy`, `FiltroCombinato`) and command execution logic for flexible query execution.

5. **DAO Pattern (`model.dao`):**
   - Abstract data access via `LibroDAO` and `LibroDAOImpl` to decouple persistence logic from business models.

---

## 📁 Repository Structure

```text
.
├── src/
│   ├── controller/      # MVC Controllers
│   ├── model/           # Business Logic, Domain Models, Enums
│   │   ├── accesslogic/ # Factory & Interface Implementations
│   │   ├── command/     # Command Pattern classes
│   │   ├── dao/         # Data Access Objects
│   │   ├── observer/    # Observer Pattern components
│   │   └── strategy/    # Strategy Pattern implementations
│   ├── view/            # Java Swing GUI Components & Dialogs
│   ├── util/            # Helper utilities and constants
│   ├── test/            # JUnit Unit Tests
│   └── MainApp.java     # Application Entry Point
├── Project external libraries/
│   ├── jackson-annotations-2.15.0.jar
│   ├── jackson-core-2.15.0.jar
│   └── jackson-databind-2.15.0.jar
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- **JDK 11** or higher
- Java IDE (Eclipse, IntelliJ IDEA, or VS Code) or command line tools

### Dependencies
The project uses Jackson libraries for serialization/deserialization, included under `Project external libraries/`:
- `jackson-annotations-2.15.0.jar`
- `jackson-core-2.15.0.jar`
- `jackson-databind-2.15.0.jar`

### Running the Application

#### Option 1: Via IDE
1. Import the repository into your preferred IDE (e.g., Eclipse / IntelliJ).
2. Ensure the JAR files in `Project external libraries/` are added to your project's Build Path / Dependencies.
3. Run `src/MainApp.java`.

#### Option 2: Via Command Line
```bash
# Compile the project with external libraries included in classpath
javac -cp "Project external libraries/*" -d bin src/**/*.java src/*.java

# Run MainApp
java -cp "bin:Project external libraries/*" MainApp
```

---

## 🧪 Running Unit Tests

The test suite covers key system behaviors including:
- `LibreriaControllerTest`
- `TestAggiornaLibro`
- `TestCapacitaMassima`
- `TestFiltraggi` & `TestFiltroCombinato`
- `TestSalvataggioCaricamento`
- `TestValidazioneInput`

Run the tests using JUnit 5 through your IDE or build runner.

---

## 📄 License

This project was developed for educational purposes as an academic assignment for the **3rd Year Bachelor's Degree in Computer Science / Software Engineering**.
