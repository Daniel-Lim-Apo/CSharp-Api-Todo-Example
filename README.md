# CSharp API Todo Example
By: Daniel Lim-Apo

## Overview
This project is a simple, straightforward ASP.NET Core Web API application that manages a "To-Do" list. It is built using **.NET 10** and demonstrates fundamental concepts of creating RESTful APIs with C# and Entity Framework Core.

The API uses an **In-Memory Database**, which means that the data is not persisted across application restarts. This makes it an excellent, lightweight example for learning and testing without needing to set up a separate database server.

## Features
*   **RESTful Architecture:** Implements standard HTTP methods (GET, POST, PUT, DELETE) for resource management.
*   **Entity Framework Core:** Uses EF Core with an In-Memory provider for data access.
*   **Minimal Configuration:** Easy to run and understand, perfect for beginners learning ASP.NET Core.
*   **Built-in HTTP Tests:** Includes `.http` files to easily test endpoints directly from your IDE (like Visual Studio or VS Code).

## Prerequisites
*   [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) or later.
*   An IDE such as [Visual Studio 2022](https://visualstudio.microsoft.com/), [Visual Studio Code](https://code.visualstudio.com/), or [JetBrains Rider](https://www.jetbrains.com/rider/).

## Getting Started

### 1. Clone the repository
Ensure you have the project cloned to your local machine.

### 2. Build the project
Navigate to the `src` directory (where the `TodoApi.csproj` file is located) and run the following command to restore dependencies and build the project:

```bash
cd src
dotnet build
```

### 3. Run the application
Start the API using the .NET CLI:

```bash
dotnet run
```

The API will start listening for requests. By default, it usually runs on `http://localhost:5000` or `https://localhost:5001`. The exact ports can be found in the console output or the `Properties/launchSettings.json` file.

## API Endpoints

The API exposes the following endpoints under the `/api/TodoItems` route:

| HTTP Method | Endpoint | Description | Request Body | Response |
| :--- | :--- | :--- | :--- | :--- |
| **GET** | `/api/TodoItems` | Retrieves a list of all to-do items. | None | `200 OK` (Array of items) |
| **GET** | `/api/TodoItems/{id}` | Retrieves a specific to-do item by its ID. | None | `200 OK` (Item) or `404 Not Found` |
| **POST** | `/api/TodoItems` | Creates a new to-do item. | JSON (Name, IsComplete) | `201 Created` (Created item) |
| **PUT** | `/api/TodoItems/{id}` | Updates an existing to-do item. | JSON (Id, Name, IsComplete) | `204 No Content` or `400/404` |
| **DELETE**| `/api/TodoItems/{id}` | Deletes a to-do item by its ID. | None | `204 No Content` or `404 Not Found` |

### Data Model (`TodoItem`)
When creating or updating an item, the JSON payload should look like this:
```json
{
  "id": 1,
  "name": "Walk the dog",
  "isComplete": false
}
```

## How to Test

You can test the API using standard tools like [Postman](https://www.postman.com/) or curl. However, this project also includes `.http` files inside the `src/Manual-Test-Http-Client` directory for quick testing directly from your code editor (requires the REST Client extension in VS Code, or built-in support in Visual Studio 2022 17.6+).

1.  Make sure the API is running (`dotnet run`).
2.  Open any of the included HTTP files located in `src/Manual-Test-Http-Client`:
    *   `TodoApi-1-POST.http` - Creates an item.
    *   `TodoApi-2-GET.http` - Fetches all items.
    *   `TodoApi-3-GET-By-Id.http` - Fetches a specific item.
    *   `TodoApi-4-PUT.http` - Updates an item.
    *   `TodoApi-5-DELETE.http` - Deletes an item.
3.  Click the **Send Request** button that appears above the HTTP request in your editor to execute it and view the response.