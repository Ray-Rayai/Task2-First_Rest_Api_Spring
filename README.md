# 1. Project Overview
This project is a simple REST API built using Spring Boot.
It demonstrates a clean, layered architecture using:
- 	Controller (API layer)
- 	Service (business logic)
- 	Repository (data access)
- 	Domain model
- 	DTOs (request/response)
- 	Mapper (object mapping)

The API allows creating Product objects and returning them as JSON

# 2.⚙️  Technologies & Dependencies

Created using Spring Initializr inside IntelliJ with:
- Spring Web
- Spring Data JPA
- H2 Database
- Spring Boot DevTools

# 3.🏗️ Project Structure
The assignment requires the following package layout:
product

firstrestapispring/
├── product/

│   ├── api/

│   │   ├── request/

│   │   │   ├── ProductRequest.java

│   │   │   └── UpdateProductRequest.java

│   │   ├── response/

│   │   │   └── ProductResponse.java

│   │   └── ProductController.java

│   ├── domain/

│   │   └── Product.java

│   ├── repository/

│   │   └── ProductRepository.java

│   ├── service/

│   │   └── ProductService.java

│   └── support/
│       ├── exception/

│       │   └── ProductNotFoundException.java

│       ├── ProductExceptionAdvisor.java

│       ├── ProductExceptionSupplier.java

│       └── ProductMapper.java

├── shared/

│   └── api/

│       └── response/

│           └── ErrorMessageResponse.java

└── FirstRestApiSpringApplication.java
        
   “Next, create a project tree (packages and classes) according to the example… For now, the classes remain empty…”

# 4.🚀 Step‑by‑Step Implementation
Step 1 — Create the project in IntelliJ
- Go to: File → New → Project → Spring Initializr
- Fill in metadata (Group, Artifact, Name).
- Add dependencies:
- Spring Web
- Spring Data JPA
- H2 Database
- Spring Boot DevTools
   Finish and let IntelliJ generate the project.
  
Step 2 — Create the Domain Model (Product)
The Product class represents the main object in the system.
- Fields: id, name
- Constructor: accepts name
- Getters & setters
This object will be stored in the repository and returned in responses.

Step 3 — Create the Repository (ProductRepository)

The repository:
-	Is annotated with @Repository
- 	Contains:
- 	Map<Long, Product> map = HashMap<>();
- 	long counter = 1;
- 	Method:
- 	save(Product entity)
- 	Assigns an ID
- 	Stores the product
- 	Returns the saved object
This simulates a database for now.

Step 4 — Create DTOs (ProductRequest & ProductResponse)
ProductRequest
Used for incoming JSON.
- Field: name
- Annotated with @JsonCreator
ProductResponse
Used for outgoing JSON.
- Fields: id, name
These classes allow the controller to receive and return clean JSON objects.

Step 5 — Create the Mapper (ProductMapper)
Responsible for converting between:
- 	ProductRequest -> Product
-	Product -> ProductResponse
Annotated with
This keeps the controller and service clean.

Step 6 — Create the Service (ProductService)

"This is a class that contain the business logic..."
Responsibilities:
1. 	Accept ProductRequest
2. 	Convert to Product using ProductMapper
3. 	Save using ProductRepository
4. 	Convert saved product to ProductResponse
5. 	Return the response to the controller
Annotated with @Service.

Step 7  Create the Controller (ProductController)
The controller:
- 	Is annotated with @ResController
- 	Injects ProjectService
- 	Exposes REST endpoints
Example endpoint (matches assignment structure):
POST /products
Request body:

<img width="517" height="251" alt="Screenshot 2026-05-09 140416" src="https://github.com/user-attachments/assets/135b9358-8ca7-4bdc-955f-ec1440edb1dc" />

Response:
     <img width="953" height="391" alt="Screenshot 2026-05-09 161233" src="https://github.com/user-attachments/assets/abc1d8b8-7778-4277-886f-e5fe54f772d4" />


The controller:
- Receives JSON → ProductRequest
- Calls service
- Returns ProductResponse as JSON

# 5.🧪 Testing the API (Postman or Swagger)

- Run the application (port 8080).
- Open Postman.
- Create a POST request:
        http://localhost:8080/products
  
- Body → raw → JSON:
{
  "name": "First product"
}

Send the request.

6. 	Verify the response contains an auto‑generated ID.

# 6.🗄️ H2 Database Console

If enabled in application.properties, you can access:

http://localhost:8080/h2-console

Use JDBC URL:
        jdbc:h2:mem:testdb
        
   <img width="1155" height="844" alt="Screenshot 2026-05-06 153723" src="https://github.com/user-attachments/assets/876b5656-87a3-42ab-97d4-80bacd6a7a63" />
     

  


        







        
