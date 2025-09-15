# Secure Payments

This repository contains a backend project showcasing a microservices architecture for a payment processing system. The solution is composed of two main services: a dedicated authentication service and a payment processing API.

## About the Project

This project was developed to demonstrate core Software Engineering principles, including:

* **Microservices Architecture:** Separating the business logic into independent, loosely coupled services.
* **Authentication and Authorization:** Implementing a secure authentication flow using JSON Web Tokens (JWT).
* **API Design:** Creating well-defined and documented APIs for seamless integration between services.
* **Dependency Management:** Showing how one service can depend on and securely consume another.

## Key Technologies

* **Backend:** ASP.NET Core with C#
* **Authentication:** JWT (JSON Web Tokens)
* **Database:** SQL Server
* **API Documentation:** Swagger/OpenAPI

## Project Structure

The solution is divided into two main projects:

* **`SecureAuth`**: The authentication service responsible for user registration and login. It issues a JWT upon successful login.
* **`PaymentContent`**: The payment processing API. It exposes endpoints to handle payment transactions, but these endpoints are protected and require a valid JWT issued by the `SecureAuth` service.

## Getting Started

Follow these steps to set up and run the project locally.

### Prerequisites

* [.NET SDK 8.0 or later](https://dotnet.microsoft.com/download)
* [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
* [Docker (Optional, but recommended)](https://www.docker.com/products/docker-desktop/)

### Setup

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/keodevspace/SecurePayments.git](https://github.com/keodevspace/SecurePayments.git)
    cd SecurePayments
    ```

2.  **Configure Database Connections**
    Open `appsettings.json` in both `SecureAuth` and `PaymentContent` and set your SQL Server connection strings.

3.  **Run Migrations**
    Run the EF Core migrations for both projects to create the necessary database tables.

4.  **Run the Services**
    Start both the `SecureAuth` and `PaymentContent` projects from your IDE (e.g., Visual Studio) or via the command line:
    ```bash
    # In the SecureAuth directory
    dotnet run

    # In a new terminal, in the PaymentContent directory
    dotnet run
    ```

### How to Use the API

Both services have **Swagger UI** enabled for easy testing and documentation.

1.  **Access Swagger:**
    * `SecureAuth`: [https://localhost:5001/swagger](https://localhost:5001/swagger) (or your local port)
    * `PaymentContent`: [https://localhost:5003/swagger](https://localhost:5003/swagger) (or your local port)

2.  **Authentication Flow**
    * **Register:** Use the `POST /api/Auth/register` endpoint on the `SecureAuth` Swagger UI to create a new user.
    * **Login:** Use the `POST /api/Auth/login` endpoint to log in. This will return a JWT. **Copy this token.**
    * **Authorize:** On the `PaymentContent` Swagger UI, click the `Authorize` button at the top and paste your JWT in the format `Bearer <token>`.
    * **Access Protected Endpoint:** Now, you can use the protected `POST /api/Payments/ProcessPayment` endpoint. Without the token, you will receive an `HTTP 401 Unauthorized` response.

## What I've Learned

* Implementing **decoupled services** and understanding the benefits of a microservices approach.
* Designing and securing APIs using **JWT authentication**.
* Creating a **production-ready workflow** with clean code and effective documentation.
