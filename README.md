# Lab Auth API

A lightweight authentication API built with Node.js, Express, and MySQL.  
It demonstrates a typical user authentication flow including signup, login, profile access, and token revocation.

---

## Overview

This project was created as a learning exercise in building secure, token-based authentication.  
It shows how a RESTful backend can:

- Register new users and store their credentials securely.
- Issue JSON Web Tokens (JWTs) on login.
- Protect routes so only authenticated users can access them.
- Revoke tokens to handle logout.

The stack uses **Express.js** for HTTP routing and **MySQL** for persistence.  
It’s designed to be easy to set up and test with tools like Postman.

---

## Setup

Make sure you have Node.js and MySQL running locally (for example through XAMPP).  
Clone or download the repository and install dependencies with `npm install`.

Create a MySQL database (for example `lab_auth`) and run the SQL schema provided in the `sql` section of this repo to create the required tables.  
Add your database credentials and JWT secret to a `.env` file (host, user, password, database name, JWT secret).

Start the server with `npm run dev`. By default it will listen on `http://localhost:3000/api`.

---

## How to run

Once the server is running you can interact with it using any HTTP client.  
Postman works well for testing because you can define an environment with a base URL (e.g. `http://localhost:3000/api`) and save variables such as a token.

Typical flow:

1. **Signup** – create a new user account by sending email, password, and other details to `/auth/signup`.
2. **Login** – authenticate with your credentials at `/auth/login` and receive a JWT token.
3. **Access protected routes** – include the token as a Bearer token in the `Authorization` header to access endpoints like `/profile`.
4. **Logout** – send a request to `/auth/logout` with the token; the token will be revoked and further use will fail.

This mirrors how most modern APIs handle authentication.

---

## Endpoints

The API was built to respond to a small set of routes.  
A health check endpoint was included so that the server and database status could be verified.  
Signup and login endpoints were provided to handle registration and authentication.  
A profile endpoint was protected by JWT and would only return data when a valid token was supplied.  
A logout endpoint revoked tokens to simulate the act of logging out.
