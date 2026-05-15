# Input Validation Demo - Node.js & Express.js

A comprehensive demonstration of input validation in a Node.js and Express.js application, focusing on security and data integrity.

## Project Overview

This application implements a user registration endpoint (`POST /api/auth/register`) with robust input validation middleware that ensures:
- Required fields are present
- Data types are correct
- Name contains only letters and spaces
- Email follows proper format
- Password meets complexity requirements

## Installation & Setup

### Prerequisites
- Node.js (v14 or higher)
- npm

### Installation Steps

1. Navigate to the project directory:
   ```bash
   cd "Input Validation Demo"
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the server:
   ```bash
   npm start
   ```

   The server will run on `http://localhost:3000`

## Project Structure

```
Input Validation Demo/
├── server.js                          # Main Express app setup
├── package.json                       # Project dependencies
├── routes/
│   └── auth.js                       # Authentication routes
├── controllers/
│   └── authController.js             # Request handlers
├── middleware/
│   └── validateRegister.js           # Input validation middleware
├── README.md                         # This file
└── TODO.md                           # Task tracking
```

## API Endpoint

### POST /api/auth/register

Registers a new user with validation.

**Request Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "SecurePass123!"
}
```

**Success Response (201):**
```json
{
  "success": true,
  "message": "User registered successfully",
  "data": {
    "name": "John Doe",
    "email": "john@example.com"
  }
}
```

**Validation Error Response (400):**
```json
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    {
      "field": "name",
      "message": "Name must contain only letters and spaces"
    }
  ]
}
```

## Validation Rules

### Name Field
- ✓ Required (must be present)
- ✓ Must contain only letters (a-z, A-Z) and spaces
- ✓ Minimum length: 2 characters
- ✓ Maximum length: 50 characters

### Email Field
- ✓ Required (must be present)
- ✓ Must match email format: `user@domain.extension`
- ✓ Uses regex: `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`
- ✓ Maximum length: 100 characters

### Password Field
- ✓ Required (must be present)
- ✓ Minimum length: 8 characters
- ✓ Maximum length: 100 characters
- ✓ Must contain at least one uppercase letter (A-Z)
- ✓ Must contain at least one lowercase letter (a-z)
- ✓ Must contain at least one digit (0-9)
- ✓ Must contain at least one special character (!@#$%^&*)

## Testing with Postman

### Test Case 1: Valid Registration (Should Succeed)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Headers:**
```
Content-Type: application/json
```
**Body (raw JSON):**
```json
{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "password": "MyPassword123!"
}
```
**Expected Response:** 201 Success

---

### Test Case 2: Missing Name Field (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{
  "email": "john@example.com",
  "password": "MyPassword123!"
}
```
**Expected Response:** 400 Validation Error  
**Expected Error Message:** "Name is required"

---

### Test Case 3: Invalid Name Format (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{
  "name": "John123",
  "email": "john@example.com",
  "password": "MyPassword123!"
}
```
**Expected Response:** 400 Validation Error  
**Expected Error Message:** "Name must contain only letters and spaces"

---

### Test Case 4: Invalid Email Format (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{
  "name": "John Doe",
  "email": "invalidemail",
  "password": "MyPassword123!"
}
```
**Expected Response:** 400 Validation Error  
**Expected Error Message:** "Email must be a valid email address"

---

### Test Case 5: Short Password (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "Pass1!"
}
```
**Expected Response:** 400 Validation Error  
**Expected Error Message:** "Password must be at least 8 characters long"

---

### Test Case 6: Password Without Uppercase (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "mypassword123!"
}
```
**Expected Response:** 400 Validation Error  
**Expected Error Message:** "Password must contain at least one uppercase letter"

---

### Test Case 7: Password Without Number (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "MyPassword!"
}
```
**Expected Response:** 400 Validation Error  
**Expected Error Message:** "Password must contain at least one number"

---

### Test Case 8: Password Without Special Character (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "MyPassword123"
}
```
**Expected Response:** 400 Validation Error  
**Expected Error Message:** "Password must contain at least one special character"

---

### Test Case 9: Multiple Validation Errors (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{
  "name": "John123",
  "email": "invalidemail",
  "password": "weak"
}
```
**Expected Response:** 400 Validation Error  
**Expected Multiple Errors**

---

### Test Case 10: Missing All Fields (Should Fail)
**Method:** POST  
**URL:** `http://localhost:3000/api/auth/register`  
**Body:**
```json
{}
```
**Expected Response:** 400 Validation Error  
**Expected Multiple Errors for all 3 fields**

---

## Testing with curl

### Valid Request
```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@example.com","password":"MyPassword123!"}'
```

### Invalid Email
```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"invalidemail","password":"MyPassword123!"}'
```

### Short Password
```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@example.com","password":"weak"}'
```

## Key Features Implemented

### ✓ Input Validation
- Comprehensive validation for all input fields
- Type checking
- Format validation with regex
- Length constraints

### ✓ Structured Error Responses
- Clear, consistent JSON response format
- Field-level error details
- Descriptive error messages

### ✓ Middleware Architecture
- Validation middleware prevents invalid data from reaching controller
- Separation of concerns
- Reusable and maintainable code

### ✓ Error Handling
- Global error handler
- 404 route handler
- Status code differentiation (400 for validation, 201 for success)

## Security Best Practices Demonstrated

1. **Input Validation** - All user inputs are validated before processing
2. **Password Complexity** - Strong password requirements enforced
3. **Type Checking** - Data types verified before use
4. **Error Messages** - Helpful but not revealing sensitive information
5. **Middleware Pattern** - Centralized validation logic

## Learning Outcomes

After completing this lab, you will have learned:

1. ✓ How to validate request body data in Express.js
2. ✓ How to create custom validation middleware
3. ✓ How to send structured JSON error responses
4. ✓ How to prevent invalid data from reaching business logic
5. ✓ Best practices for API security and data integrity
6. ✓ Practical input validation patterns and techniques

## Future Enhancements

- Add database integration to store registered users
- Implement password hashing with bcrypt
- Add email verification flow
- Implement rate limiting for registration
- Add JWT authentication
- Create login endpoint with validation
- Add more comprehensive error logging

## Notes

- This is a demonstration project for learning purposes
- In production, use established validation libraries like `joi` or `yup`
- Always hash passwords before storing them
- Implement rate limiting to prevent abuse
- Use HTTPS in production
- Validate on both client and server side

## Author
Input Validation Demo Lab
