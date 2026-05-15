# Test Examples - Ready to Copy/Paste into Postman

## ✓ VALID TEST CASES (Should Return 201)

### Test 1: Basic Valid Registration
```json
{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "password": "MyPassword123!"
}
```

### Test 2: Another Valid User
```json
{
  "name": "Jane Smith",
  "email": "jane.smith@gmail.com",
  "password": "SecurePass456@"
}
```

### Test 3: Valid User with Long Password
```json
{
  "name": "Alice Johnson",
  "email": "alice.johnson@company.com",
  "password": "VeryLongPassword123!SecureWithSymbol"
}
```

### Test 4: Valid User with Multiple Words in Name
```json
{
  "name": "Mary Jane Watson",
  "email": "mary.jane@webmail.com",
  "password": "Complex@Pass789"
}
```

---

## ✗ INVALID TEST CASES (Should Return 400)

### Test 5: Missing Name Field
```json
{
  "email": "john@example.com",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Name is required"

---

### Test 6: Name with Numbers
```json
{
  "name": "John123",
  "email": "john@example.com",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Name must contain only letters and spaces"

---

### Test 7: Name Too Short
```json
{
  "name": "J",
  "email": "john@example.com",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Name must be at least 2 characters long"

---

### Test 8: Name with Special Characters
```json
{
  "name": "John@Doe#",
  "email": "john@example.com",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Name must contain only letters and spaces"

---

### Test 9: Missing Email Field
```json
{
  "name": "John Doe",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Email is required"

---

### Test 10: Invalid Email Format (No @)
```json
{
  "name": "John Doe",
  "email": "johndomain.com",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Email must be a valid email address"

---

### Test 11: Invalid Email Format (No Domain)
```json
{
  "name": "John Doe",
  "email": "john@",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Email must be a valid email address"

---

### Test 12: Email with Spaces
```json
{
  "name": "John Doe",
  "email": "john @example.com",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Email must be a valid email address"

---

### Test 13: Missing Password Field
```json
{
  "name": "John Doe",
  "email": "john@example.com"
}
```
**Expected Error:** "Password is required"

---

### Test 14: Password Too Short
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "Pass1!"
}
```
**Expected Error:** "Password must be at least 8 characters long"

---

### Test 15: Password Without Uppercase Letter
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "mypassword123!"
}
```
**Expected Error:** "Password must contain at least one uppercase letter"

---

### Test 16: Password Without Lowercase Letter
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "MYPASSWORD123!"
}
```
**Expected Error:** "Password must contain at least one lowercase letter"

---

### Test 17: Password Without Number
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "MyPassword!"
}
```
**Expected Error:** "Password must contain at least one number"

---

### Test 18: Password Without Special Character
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "MyPassword123"
}
```
**Expected Error:** "Password must contain at least one special character"

---

### Test 19: All Fields Missing
```json
{}
```
**Expected Errors:** Multiple - missing name, email, and password

---

### Test 20: Multiple Validation Errors
```json
{
  "name": "John123",
  "email": "invalidemail",
  "password": "weak"
}
```
**Expected Errors:** 
- Invalid name (contains numbers)
- Invalid email format
- Password too short
- Password missing uppercase
- Password missing special character

---

### Test 21: Empty String Values
```json
{
  "name": "",
  "email": "",
  "password": ""
}
```
**Expected Error:** Fields must be non-empty strings

---

### Test 22: Null Values
```json
{
  "name": null,
  "email": null,
  "password": null
}
```
**Expected Error:** Type validation errors

---

### Test 23: Non-String Name
```json
{
  "name": 123,
  "email": "john@example.com",
  "password": "MyPassword123!"
}
```
**Expected Error:** "Name must be a non-empty string"

---

### Test 24: Non-String Email
```json
{
  "name": "John Doe",
  "email": 123,
  "password": "MyPassword123!"
}
```
**Expected Error:** "Email must be a non-empty string"

---

### Test 25: Non-String Password
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": 123
}
```
**Expected Error:** "Password must be a non-empty string"

---

## Instructions for Use

1. **Open Postman**
2. **Create New Request**
   - Method: POST
   - URL: `http://localhost:3000/api/auth/register`
   - Headers: `Content-Type: application/json`

3. **Copy Test Case Body**
   - Copy the JSON from one of the examples above
   - Paste into Postman's "Body" tab (raw, JSON)

4. **Send Request**
   - Click "Send"
   - Review the response status and body

5. **Expected Results**
   - ✓ Valid cases: **201 Created** with success message
   - ✗ Invalid cases: **400 Bad Request** with validation errors

## Summary Statistics

- **Valid Test Cases:** 4
- **Invalid Test Cases:** 21
- **Total Test Cases:** 25

## Special Characters Allowed in Password

```
! @ # $ % ^ & * ( ) _ + - = [ ] { } ; ' : " \ | , . < > / ?
```

At least one is required for password validation.
