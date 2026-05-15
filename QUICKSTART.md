# Quick Start Guide

## 🚀 Getting Started

### Step 1: Install Node.js
If you don't have Node.js installed, download it from https://nodejs.org/ (LTS version recommended)

### Step 2: Navigate to Project Directory
```bash
cd "Input Validation Demo"
```

### Step 3: Install Dependencies
```bash
npm install
```

This will install Express.js and create a `node_modules` folder.

### Step 4: Start the Server
```bash
npm start
```

You should see:
```
Server is running on http://localhost:3000
```

## 🧪 Testing the API

### Method 1: Using Postman (Recommended)
1. Download Postman from https://www.postman.com/
2. Create a new POST request to `http://localhost:3000/api/auth/register`
3. Set header: `Content-Type: application/json`
4. Use the test cases in README.md

### Method 2: Using curl (Command Line)

**Valid request:**
```bash
curl -X POST http://localhost:3000/api/auth/register ^
  -H "Content-Type: application/json" ^
  -d "{\"name\":\"John Doe\",\"email\":\"john@example.com\",\"password\":\"MyPassword123!\"}"
```

**Invalid request (missing name):**
```bash
curl -X POST http://localhost:3000/api/auth/register ^
  -H "Content-Type: application/json" ^
  -d "{\"email\":\"john@example.com\",\"password\":\"MyPassword123!\"}"
```

## 📊 Expected Results

### ✓ Valid Input
- Status: **201 Created**
- Response includes success message and user data

### ✗ Invalid Input
- Status: **400 Bad Request**
- Response includes validation errors array with field details

## 📋 Validation Rules Summary

| Field | Requirements |
|-------|--------------|
| **Name** | Letters/spaces only, 2-50 chars |
| **Email** | Valid format (user@domain.ext), max 100 chars |
| **Password** | 8-100 chars, uppercase, lowercase, number, special char |

## 🛑 To Stop the Server
Press `Ctrl+C` in the terminal

## 📚 File Structure Overview

```
Input Validation Demo/
├── server.js                 # Main Express application
├── package.json             # Project dependencies
├── .gitignore              # Git ignore file
├── README.md               # Full documentation
├── routes/
│   └── auth.js            # /api/auth/register endpoint
├── controllers/
│   └── authController.js   # Registration handler logic
└── middleware/
    └── validateRegister.js # Input validation middleware
```

## 💡 Key Learning Points

1. **Validation Middleware** - Validates before controller executes
2. **Structured Errors** - Clear error responses for debugging
3. **Security** - Input validation prevents invalid/malicious data
4. **Separation of Concerns** - Routes, controllers, middleware are separate

## 🐛 Troubleshooting

### Port Already in Use
If port 3000 is already used, change it:
```bash
set PORT=3001 && npm start
```

### npm Command Not Found
Reinstall Node.js and add it to your system PATH

### Module Not Found Error
Run `npm install` again and verify node_modules folder exists

## ✨ Next Steps

1. Install Node.js
2. Run `npm install`
3. Run `npm start`
4. Test with Postman or curl
5. Review the validation logic in middleware/validateRegister.js
6. Experiment with different inputs

Happy learning! 🎓
