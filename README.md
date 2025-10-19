🚀 Task 1 – Spring Boot + MongoDB Application


<img width="2226" height="1301" alt="image" src="https://github.com/user-attachments/assets/a7a4370a-be65-4773-827f-1213e96816bf" />


Welcome to Task 1! 🎯
This project demonstrates a simple Spring Boot REST API integrated with MongoDB, containerized using Docker for smooth deployment. 💻⚙️

🧰 Tech Stack
Tool	Purpose
☕ Java	Core programming language
🌱 Spring Boot	REST API framework
🧩 Maven	Build and dependency management
🍃 MongoDB	NoSQL database
🐳 Docker	Containerization
📦 Dependencies

The following Maven dependencies are used in this project:

- spring-boot-starter-web
- spring-boot-starter-data-mongodb
- spring-boot-starter-test
- spring-boot-maven-plugin

🧑‍💻 How to Build and Run
🪜 Step-by-Step Guide

Open the project

Navigate to the /task1 folder

Open it in your favorite IDE (VS Code ❤️ or IntelliJ)

Build the project

mvn clean install


This will compile your code, run tests, and create a JAR file inside the /target folder.

Run the Application

Use the IDE’s Run ▶️ option or press F9

The Spring Boot server will start on:
🌐 http://localhost:8080

🌍 API Endpoints

The base endpoint for the REST API is:

http://127.0.0.1:8080/servers/

Method	Endpoint	Description
🟩 PUT	/servers/	Create or update a server (JSON body required)
🟦 GET	/servers/GET	Fetch all servers
🟦 GET	/servers/GET?id=<ID>	Fetch a single server by ID
🟦 GET	/servers/GET?name=<Name>	Fetch servers by name
🟥 DELETE	/servers/DELETE?id=<ID>	Delete a server by ID
🧩 Repository Interface

Your ServerRepository extends MongoRepository and provides handy methods:

List<Server> findAll();
Optional<Server> findById(String id);
void createOrUpdateServer(Server server);
void deleteServerById(String id);
List<Server> findByName(String name);

🐳 Containerizing with Docker

Here’s the Dockerfile used to containerize the app:

FROM openjdk:8-alpine
EXPOSE 8080
ADD target/demo.jar demo.jar
ENTRYPOINT ["java", "-Dspring.data.mongodb.uri=mongodb://mongod:27017/servers", "-jar", "/demo.jar"]

⚙️ Build Docker Image
sudo docker build -t <image_name> .


✅ This will create a Docker image and store it locally.

▶️ Run the Container
sudo docker run -p 8080:8080 <image_name>


Your Spring Boot app will start on port 8080 🖥️
Check your terminal for live logs and startup messages. 🧾

💡 Note: The Docker Compose configuration is documented in Task 3.

🧪 Testing APIs with Postman

You can test the REST APIs easily using Postman 👇

Important:
This collection is tested for the base endpoint
👉 http://127.0.0.1:8080/servers/

📸 Screenshots
