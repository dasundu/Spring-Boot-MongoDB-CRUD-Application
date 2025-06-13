Spring Boot MongoDB CRUD Application
A simple RESTful web service built with Spring Boot and MongoDB that demonstrates CRUD (Create, Read, Update, Delete) operations for user management.
📋 Table of Contents

Overview
Features
Technologies Used
Prerequisites
Installation & Setup
Project Structure
API Endpoints
Usage Examples
Configuration
Testing
Contributing

🎯 Overview
This project is a Spring Boot application that provides a REST API for managing user data stored in MongoDB. It implements the Model-View-Controller (MVC) architecture pattern and demonstrates best practices for building microservices with Spring Boot.
The application allows you to:

Create new users
Retrieve all users or a specific user by ID
Update existing user information
Delete users from the database

✨ Features

RESTful API: Clean REST endpoints following HTTP standards
MongoDB Integration: NoSQL database for flexible data storage
CRUD Operations: Complete Create, Read, Update, Delete functionality
Error Handling: Proper HTTP status codes and error responses
Data Validation: Input validation and error handling
Auto-Configuration: Spring Boot's automatic configuration for MongoDB
JSON Support: Automatic JSON serialization/deserialization

🛠 Technologies Used

Java 11+: Programming language
Spring Boot 3.x: Application framework
Spring Data MongoDB: MongoDB integration
Spring Web: REST API development
MongoDB: NoSQL database
Maven: Dependency management and build tool
Jackson: JSON processing

📋 Prerequisites
Before running this application, make sure you have the following installed:

Java Development Kit (JDK) 11 or higher
Maven 3.6+
MongoDB 4.4+ (running on localhost:27017)
Git (for cloning the repository)
Postman or curl (for testing APIs)

🚀 Installation & Setup
1. Clone the Repository
bashgit clone https://github.com/yourusername/spring-mongodb-crud.git
cd spring-mongodb-crud
2. Start MongoDB
Make sure MongoDB is running on your system:
bash# On Windows
net start MongoDB

# On macOS/Linux
sudo systemctl start mongod
# or
brew services start mongodb-community
3. Build the Project
bashmvn clean install
4. Run the Application
bashmvn spring-boot:run
Or run directly:
bashjava -jar target/lab7-0.0.1-SNAPSHOT.jar
The application will start on http://localhost:8080
📁 Project Structure
src/
├── main/
│   ├── java/com/example/lab7/
│   │   ├── Lab7Application.java          # Main application class
│   │   ├── controller/
│   │   │   └── UserController.java       # REST endpoints
│   │   ├── model/
│   │   │   └── User.java                 # User entity/model
│   │   ├── repository/
│   │   │   └── UserRepository.java       # Data access layer
│   │   └── service/
│   │       └── UserService.java          # Business logic layer
│   └── resources/
│       └── application.properties        # Configuration file
├── pom.xml                              # Maven dependencies
└── README.md                            # Project documentation
🔗 API Endpoints
MethodEndpointDescriptionRequest BodyGET/usersGet all usersNoneGET/users/{id}Get user by IDNonePOST/usersCreate new userUser JSONPUT/users/{id}Update userUser JSONDELETE/users/{id}Delete userNone
User JSON Format
json{
    "name": "John Doe",
    "age": 30,
    "email": "john.doe@example.com"
}
💡 Usage Examples
Create a New User
bashcurl -X POST http://localhost:8080/users \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Alice Johnson",
    "age": 28,
    "email": "alice@example.com"
  }'
Get All Users
bashcurl -X GET http://localhost:8080/users
Get User by ID
bashcurl -X GET http://localhost:8080/users/60f7b1b9e4b0a73d4c8b4567
Update a User
bashcurl -X PUT http://localhost:8080/users/60f7b1b9e4b0a73d4c8b4567 \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Alice Smith",
    "age": 29,
    "email": "alice.smith@example.com"
  }'
Delete a User
bashcurl -X DELETE http://localhost:8080/users/60f7b1b9e4b0a73d4c8b4567
⚙️ Configuration
Application Properties
The application configuration is in src/main/resources/application.properties:
properties# Application name
spring.application.name=lab7

# MongoDB configuration
spring.data.mongodb.database=lab7
spring.data.mongodb.port=27017
spring.data.mongodb.host=localhost

# Optional: Server port (default is 8080)
# server.port=8080
MongoDB Database

Database Name: lab7
Collection Name: users
Connection: localhost:27017

🧪 Testing
Using Postman

Import the API endpoints into Postman
Set the base URL to http://localhost:8080
Test each endpoint with appropriate request bodies

Using MongoDB Compass

Connect to mongodb://localhost:27017
Navigate to the lab7 database
View the users collection to see stored data

Sample Test Data
json[
  {
    "name": "John Doe",
    "age": 30,
    "email": "john@example.com"
  },
  {
    "name": "Jane Smith",
    "age": 25,
    "email": "jane@example.com"
  },
  {
    "name": "Bob Johnson",
    "age": 35,
    "email": "bob@example.com"
  }
]
🔧 Troubleshooting
Common Issues

MongoDB Connection Error

Ensure MongoDB is running on localhost:27017
Check if the database name matches in application.properties


Port Already in Use

Change the server port in application.properties: server.port=8081


Maven Build Failures

Ensure Java 11+ is installed
Run mvn clean install to resolve dependencies


JSON Parsing Errors

Verify request headers include Content-Type: application/json
Check JSON syntax in request bodies



📚 Learning Objectives
This project demonstrates:

Spring Boot fundamentals and auto-configuration
RESTful API design principles
MongoDB integration with Spring Data
Layered architecture (Controller → Service → Repository)
Dependency injection and inversion of control
HTTP status codes and error handling
JSON serialization/deserialization

🤝 Contributing

Fork the repository
Create a feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add some amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request

📝 License
This project is created for educational purposes as part of the SE3040 Application Frameworks course.


Happy Coding! 🚀
