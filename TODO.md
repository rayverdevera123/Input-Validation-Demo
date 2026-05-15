# TODO - Input Validation Demo

## Step 1
- Create project structure and initialize npm (package.json)

## Step 2
- Install Express and add start script

## Step 3
- Create Express server entry point (server.js)

## Step 4
- Create route POST /register (routes/auth.js)

## Step 5
- Create controller (controllers/authController.js) with no validation logic

## Step 6
- Create validation middleware (middleware/validateRegister.js)
  - Validate name (letters + spaces)
  - Validate email (regex + presence)
  - Validate password (complexity + presence)
  - Return structured JSON errors

## Step 7
- Create README.md with Postman test cases

## Step 8
- Run quick functional test via curl/Postman + ensure invalid requests don’t hit controller

