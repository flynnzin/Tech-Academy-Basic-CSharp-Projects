# DIO.Series - TV Series Management Console Application

## Overview

DIO.Series is a **console-based TV series management application** built with C#. It demonstrates fundamental object-oriented programming (OOP) concepts including inheritance, interfaces, repositories, and enums. This project was created as part of a Digital Innovation One (DIO) learning course.

## Purpose

This application serves as an educational project to teach:
- **Object-Oriented Programming (OOP)**: Classes, inheritance, encapsulation
- **Repository Pattern**: Data persistence and retrieval abstraction
- **Enumerations**: Type-safe enum usage for categories
- **Console I/O**: User interaction through command-line interface
- **CRUD Operations**: Create, Read, Update, Delete functionality

## Features

- 📺 **Add TV Series**: Insert new series to the collection
- 🔍 **List Series**: View all registered series
- 📝 **Update Series**: Modify series information
- 🗑️ **Delete Series**: Remove series from the collection
- 👁️ **View Details**: Display complete series information
- 🎬 **Genre Classification**: Series categorized by genre

## Project Structure

```
projeto_dotnet/
├── Program.cs                        # Main application entry point
├── DIO.Series.csproj               # Project configuration (.NET Core 3.1)
├── Classes/
│   ├── EntidadeBase.cs             # Base class with common properties
│   ├── Serie.cs                    # TV Series entity class
│   └── SerieRepositorio.cs         # Data repository for series
├── Enum/
│   └── Genero.cs                   # Genre enumeration
├── Interfaces/
│   └── IRepositorio.cs             # Repository interface contract
├── bin/
│   └── Debug/netcoreapp3.1/        # Compiled application
└── obj/
    └── Debug/netcoreapp3.1/        # Object files and metadata

```

## Core Classes

### EntidadeBase
Base class that provides common properties for all entities:
- **Id**: Unique identifier for each entity

```csharp
public class EntidadeBase
{
    public int Id { get; set; }
}
```

### Serie (TV Series)
Represents a television series with the following properties:
- **Id**: Unique identifier (inherited)
- **Genero**: Genre/Category (Enum)
- **Titulo**: Series title
- **Descricao**: Series description
- **Ano**: Starting year
- **Excluido**: Deletion flag (soft delete)

Methods:
- `ToString()`: Formatted display of series information
- `retornaTitulo()`: Get series title
- `retornaId()`: Get series ID
- `retornaExcluido()`: Check if series is deleted
- `Excluir()`: Mark series as deleted

### Genero (Genre Enum)
Categories for series classification:
- Action
- Comedy
- Drama
- Horror
- Romance
- Thriller
- And more...

### SerieRepositorio (Repository)
Implements the Repository Pattern to manage series data:
- **InserirSerie()**: Add a new series
- **ListarSeries()**: Retrieve all series
- **AtualizarSerie()**: Modify existing series
- **ExcluirSerie()**: Delete a series
- **ObterSeriePorId()**: Find series by ID

### IRepositorio (Interface)
Contract interface defining repository operations:
```csharp
public interface IRepositorio<T>
{
    void Inserir(T entidade);
    List<T> Listar();
    void Atualizar(int id, T entidade);
    void Excluir(int id);
}
```

## Menu Options

When you run the application, you'll see the following menu:

```
1. List Series
2. Add Series
3. Update Series
4. Delete Series
5. View Series Details
C. Clear Screen
X. Exit Application
```

### Workflow Examples

**Adding a Series:**
1. Select option "2"
2. Enter genre number (1-10)
3. Enter series title
4. Enter series description
5. Enter starting year

**Viewing a Series:**
1. Select option "5"
2. Enter the series ID
3. Displays all series details

**Updating a Series:**
1. Select option "3"
2. Enter series ID to update
3. Follow prompts to modify series information

## Technical Stack

- **Language**: C# 8.0+
- **Framework**: .NET Core 3.1
- **Application Type**: Console Application
- **Architecture Pattern**: Repository Pattern
- **Design Principles**: SOLID principles

## Prerequisites

- .NET Core 3.1 SDK or later
- Windows, macOS, or Linux
- A terminal or command prompt

## Running the Application

### Via Command Line:
```powershell
cd projeto_dotnet
dotnet run
```

### Via Visual Studio:
1. Open `DIO.Series.csproj`
2. Press `F5` or click "Start Debugging"
3. Follow the on-screen menu prompts

## Code Example

```csharp
// Create a new series instance
Serie novasSerie = new Serie(
    id: 1,
    genero: Genero.Drama,
    titulo: "Breaking Bad",
    descricao: "A high school chemistry teacher...",
    ano: 2008
);

// Insert into repository
repositorio.Inserir(novasSerie);

// List all series
List<Serie> todasAsSeries = repositorio.Listar();

// Update a series
repositorio.Atualizar(1, serieAtualizada);

// Delete a series
repositorio.Excluir(1);
```

## Learning Objectives Covered

✅ Object-Oriented Programming (OOP)
✅ Class Inheritance
✅ Interface Implementation
✅ Enumeration Usage
✅ Repository Design Pattern
✅ Encapsulation and Access Modifiers
✅ Collections (Lists, Arrays)
✅ Console I/O Operations
✅ String Manipulation
✅ Exception Handling

## Scope

This is an **educational project** demonstrating fundamental C# concepts. It uses in-memory storage and does not persist data to a database between sessions.

## Future Enhancements

Possible improvements for learning purposes:
- Database integration (Entity Framework Core)
- File-based persistence (JSON/XML)
- Graphical User Interface (WPF/Windows Forms)
- Unit Testing (xUnit/NUnit)
- API wrapper (ASP.NET Core)


**Digital Innovation One (DIO)**  
Educational programming course project

## License

This project is provided for educational purposes. Feel free to use, modify, and learn from this code.

---

**Note**: This is a beginner-to-intermediate level C# learning project. It's ideal for understanding core OOP concepts and the Repository Pattern before advancing to more complex applications.



# MenuAPI - Advanced Menu System for C#

## Overview

MenuAPI is a comprehensive menu management library designed for C# resources in gaming environments. It supports both **FiveM** and **RedM** platforms, providing developers with an advanced, user-friendly interface for creating interactive menus.

## Features

- **Multi-Platform Support**: Works seamlessly with FiveM and RedM C# resources
- **Rich Menu Items**: Multiple item types including:
  - Basic Menu Items
  - Checkbox Items (toggleable options)
  - List Items (dropdown selections)
  - Dynamic List Items (list items with dynamic content)
  - Slider Items (numerical value selection)
- **Event-Driven Architecture**: Comprehensive event system for item selection, checkbox toggling, list changes, and slider adjustments
- **Menu Controller**: Centralized management of multiple menus
- **Flexible Configuration**: Customizable menu appearance and behavior

## Project Structure

```
Menu-Csharp/
├── MenuAPI/                          # Main library project
│   ├── Menu.cs                       # Core Menu class with event handling
│   ├── MenuController.cs             # Controller for managing multiple menus
│   ├── MenuAPI.csproj               # Project configuration
│   ├── MenuAPI.nuspec               # NuGet package specification
│   └── items/                        # Menu item types
│       ├── MenuItem.cs               # Base menu item
│       ├── MenuCheckboxItem.cs       # Checkbox item type
│       ├── MenuListItem.cs           # List selection item
│       ├── MenuDynamicListItem.cs    # Dynamic list item
│       └── MenuSliderItem.cs         # Slider item for numeric selection
├── TestMenu/                         # Example implementation
│   ├── ExampleMenu.cs               # Sample menu usage
│   └── TestMenu.csproj              # Test project configuration
├── shared/                           # Shared resources
│   └── RedM/
│       └── Controls.cs              # RedM control definitions
├── dependencies/                     # External dependencies
│   └── RedM/
│       └── CitizenFX.Core.xml       # CitizenFX core library
├── MenuAPI.sln                       # Solution file
└── appveyor.yml                      # CI/CD configuration

```

## Key Components

### Menu Class
The core class that handles menu creation and management. It provides:
- Event delegates for item selection, checkbox changes, and list selections
- Menu state management
- Event triggering mechanism

### Menu Items
Various item types for different interaction patterns:
- **MenuItem**: Basic clickable item
- **MenuCheckboxItem**: Toggle between true/false states
- **MenuListItem**: Select from a list of predefined options
- **MenuDynamicListItem**: List items with dynamic content
- **MenuSliderItem**: Numeric value selection with min/max bounds

### MenuController
Manages multiple menu instances and handles their coordination.

## Target Framework

- **.NET Framework 4.5.2** (net452)
- Compatible with FiveM and RedM resource systems

## Usage Example

```csharp
// Create a new menu
Menu myMenu = new Menu("Title", "Subtitle");

// Add different item types
MenuItem basicItem = new MenuItem("Click Me");
MenuCheckboxItem checkboxItem = new MenuCheckboxItem("Option", false);
MenuListItem listItem = new MenuListItem("Choose", new List<string> { "Option 1", "Option 2" });

myMenu.AddMenuItem(basicItem);
myMenu.AddMenuItem(checkboxItem);
myMenu.AddMenuItem(listItem);

// Subscribe to events
myMenu.OnItemSelect += (menu, item, index) => {
    // Handle item selection
};

myMenu.OnCheckboxChange += (menu, item, index, newState) => {
    // Handle checkbox toggle
};
```

## License

This project is licensed under a custom license. Key provisions:
- ✅ Use and modify freely
- ✅ Include in your projects with proper credit
- ❌ Cannot be sold or monetized
- ❌ Must provide free access if included in paid resources
- ❌ Cannot be relaunched without fork
- Must maintain license and provide attribution
 
For modifications or special permissions, please contact the original author.

## Build & Deployment

The project uses AppVeyor for CI/CD:
- Automatic builds on commit
- Support for multiple configurations (Debug/Release for both FiveM and RedM)
- Automated deployment scripts

## Dependencies

- CitizenFX.Core (included in dependencies folder)
- .NET Framework 4.5.2+

## Support

For issues, questions, or feature requests, visit the GitHub repository or contact the author directly.

---

**Note**: This is an advanced menu API designed for experienced C# developers working with FiveM/RedM. Familiarity with C# and the CitizenFX framework is recommended.
