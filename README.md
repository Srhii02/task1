
🚀 Task 1 – Spring Boot + MongoDB Application


https://github.com/user-attachments/assets/1b93fb5e-ffd7-445b-b718-f35d168783a6


🎯 Overview

This project demonstrates a Spring Boot REST API integrated with MongoDB, built and packaged using Maven, and containerized with Docker for seamless deployment.

It’s a beginner-friendly full-stack backend setup to help understand how a modern Java-based microservice works — from coding to containerization! 💻⚙️


🧰 Tech Stack
Tool	Purpose
☕ Java	Core programming language
🌱 Spring Boot	Framework for REST API development
🧩 Maven	Build automation & dependency management
🍃 MongoDB	NoSQL database for server records
🐳 Docker	Containerization and deployment



📦 Project Structure
📁 task1/
├── 📂 src/
│   ├── 📂 main/
│   │   ├── 📂 java/com/example/demo/
│   │   │   ├── DemoApplication.java        # Main Spring Boot entry point
│   │   │   ├── controller/ServerController.java
│   │   │   ├── model/Server.java
│   │   │   ├── repository/ServerRepository.java
│   │   │   └── service/ServerService.java
│   │   └── 📂 resources/
│   │       ├── application.properties      # MongoDB config
│   │       └── static/ & templates/ (optional)
│   └── 📂 test/                            # JUnit tests
├── 📄 pom.xml                              # Maven dependencies
├── 📄 Dockerfile                           # Docker configuration
└── 📄 README.md                            # Project documentation

📚 Maven Dependencies

The project uses the following key dependencies in pom.xml:

<dependencies>
    <!-- Web layer for REST APIs -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- MongoDB database support -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-mongodb</artifactId>
    </dependency>

    <!-- Testing framework -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>

⚙️ How to Build & Run

Follow these steps carefully 👇

🪜 Step 1: Clone the Repository
git clone https://github.com/<your-username>/task1.git
cd task1

🪜 Step 2: Build the Project

Run Maven build command:

mvn clean install


✅ This command will:

Clean old builds

Compile the source code

Run unit tests

Generate a runnable JAR file under target/demo.jar

🪜 Step 3: Run the Application (Locally)

You can run the Spring Boot app using your IDE (IntelliJ / VS Code) or terminal:

java -jar target/demo.jar


🌐 Server will start on:
http://localhost:8080

🌍 REST API Endpoints
Method	Endpoint	Description
🟩 PUT	/servers/	Create or update a server (JSON body required)
🟦 GET	/servers/GET	Fetch all servers
🟦 GET	/servers/GET?id=<ID>	Fetch a single server by ID
🟦 GET	/servers/GET?name=<Name>	Fetch servers by name
🟥 DELETE	/servers/DELETE?id=<ID>	Delete a server by ID

Base URL:
👉 http://127.0.0.1:8080/servers/

🧩 Repository Interface

ServerRepository extends MongoRepository and provides CRUD operations:

public interface ServerRepository extends MongoRepository<Server, String> {
    List<Server> findAll();
    Optional<Server> findById(String id);
    List<Server> findByName(String name);
    void deleteServerById(String id);
}

🐳 Docker Integration

The project includes a Dockerfile to containerize the Spring Boot app and connect it with MongoDB.

🧾 Dockerfile
FROM openjdk:8-alpine
EXPOSE 8080
ADD target/demo.jar demo.jar
ENTRYPOINT ["java", "-Dspring.data.mongodb.uri=mongodb://mongod:27017/servers", "-jar", "/demo.jar"]

🏗️ Build Docker Image
sudo docker build -t springboot-mongo-app .


✅ This creates a Docker image named springboot-mongo-app locally.

▶️ Run Docker Container
sudo docker run -p 8080:8080 springboot-mongo-app


🌍 The app will be live at:
👉 http://localhost:8080

Check container logs for live status updates. 🧾

💡 Docker Compose configuration is covered in Task 3.

🧪 Testing with Postman

You can test all endpoints using Postman:

Set Base URL → http://127.0.0.1:8080/servers/

Use PUT, GET, and DELETE requests as per the endpoints above.

🧩 Example Request (PUT):

{
  "id": "1",
  "name": "Backend Server",
  "Owner":"Srujana",
  "command": "Running"
}

📸 Screenshots

<img width="2226" height="1301" alt="image" src="https://github.com/user-attachments/assets/a7a4370a-be65-4773-827f-1213e96816bf" />


🧠 Key Takeaways

✅ Learn how to integrate Spring Boot with MongoDB
✅ Understand CRUD operations via REST APIs
✅ Gain experience with Maven builds
✅ Learn how to containerize Spring Boot apps using Docker

💬 Author

👨‍💻 Srujana Srhii Tarigoppula
🎓 B.Tech CSE-AI @ Amrita Vishwa Vidyapeetham
📍 Amaravati, India
