### **README.md for Contact Management System**

---

# **Contact Management System**

A simple and secure contact management system with authentication using JSON Web Tokens (JWT). The project is built using ASP.NET Core, Entity Framework Core, React for the frontend, and hosted on Azure. It also includes Swagger for API testing and documentation.

---

## **Features**

- **User Authentication:**
  - Secure login with JWT tokens.
  - Role-based access control for API endpoints.
- **Contact Management:**
  - Add, update, view, and delete contacts.
  - Contacts are linked to individual authenticated users.
- **API Documentation:**
  - Integrated Swagger UI for testing and exploring API endpoints.
- **Database Integration:**
  - Uses SQL Server for storing user and contact data.


---

## **Technologies Used**

### Backend:
- ASP.NET Core
- Entity Framework Core
- JWT for authentication
- SQL Server

### Tools:
- Swagger
- Azure Cloud for hosting

---

## **Getting Started**

### Prerequisites
1. [.NET 6 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)
2. [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)


---

## **Setup Instructions**

### Backend Setup

1. **Clone the Repository:**
   bash
   git clone <repository-url>
   cd ContactManagement
   

2. **Configure Database Connection:**
   Update the `appsettings.json` file with your SQL Server connection string:
   json
   "ConnectionStrings": {
       "DefaultConnection": "Server=YOUR_SERVER_NAME;Database=Contact;Trusted_Connection=True;MultipleActiveResultSets=true"
   }
   

3. **Run Database Migrations:**
   Ensure the database is created and up to date:
   bash
   dotnet ef database update
   

4. **Run the Backend:**
   bash
   dotnet run
   

5. **Access Swagger UI:**
   Navigate to `https://localhost:<port>` in your browser (replace `<port>` with the actual port number) to test the API.

---
## **Database Design**

### Tables

#### **Users**
| Column Name      | Data Type    | Description                    |
|-------------------|-------------|--------------------------------|
| `Id`             | INT         | Primary key.                  |
| `Username`       | NVARCHAR    | Unique username for login.    |
| `PasswordHash`   | NVARCHAR    | Hashed password.              |

#### **Contacts**
| Column Name      | Data Type    | Description                    |
|-------------------|-------------|--------------------------------|
| `Id`             | INT         | Primary key.                  |
| `Name`           | NVARCHAR    | Name of the contact.          |
| `Number`         | NVARCHAR    | Contact's phone number.       |
| `Address`        | NVARCHAR    | Contact's address.            |
| `UserId`         | INT         | Foreign key linking to Users. |

### Run query for create database:-
   - create database Contact
   
     CREATE TABLE Users (
    Id INT PRIMARY KEY IDENTITY,
    Username NVARCHAR(100) NOT NULL UNIQUE,
    PasswordHash NVARCHAR(MAX) NOT NULL
);

-insert admin user

INSERT INTO Users (Username, PasswordHash)
VALUES ('testuser', '$2a$12$E2NZWQxHUfNvY5D/h7Unle2zTWG9H1N/td/M8oK4F/TAQpOFi/G3W'); -- Password is 'password' hashed with BCrypt

CREATE TABLE Contacts (
    Id INT PRIMARY KEY IDENTITY,
    UserId INT NOT NULL FOREIGN KEY REFERENCES Users(Id),
    Name NVARCHAR(100),
    Number NVARCHAR(20),
    Address NVARCHAR(200)
);


### Relationships
- `Users` and `Contacts` have a one-to-many relationship.
- Each contact belongs to a specific user.

---

## **Testing the Application**

1. **Swagger Testing:**
   - Use the Swagger UI at `https://<your-backend-url>/swagger` for API testing.
   - Authorize using a JWT token to test protected routes.

---

## **Contributing**

1. Fork the repository.
2. Create a feature branch:
   bash
   git checkout -b feature/your-feature
   
3. Commit changes:
   bash
   git commit -m "Add your message"
   
4. Push to the branch:
   bash
   git push origin feature/your-feature
   
5. Submit a pull request.

---

## **License**

This project is licensed under the MIT License. See the LICENSE file for details.

---

## **Contact**

For questions or support, feel free to contact the project maintainer:

**Rohit mangal**  
[LinkedIn](https://www.linkedin.com/in/rohit-mangal-31136a19b/)  
Email: rohitmangal841@gmail.com
