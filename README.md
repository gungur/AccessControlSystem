# Access Control System

## Overview

This Java program implements a simple access control system that manages user authentication and authorization. The system allows for user management (adding, removing, modifying users) with different privilege levels (admin vs regular users).

## Classes

### 1. User Class
- Represents a user with username, password, and admin status
- **Key Methods**:
  - `isValidLogin()`: Verifies if provided password matches user's password
  - `getUsername()`: Returns the username
  - `getIsAdmin()`: Returns admin status
  - `setPassword()`: Updates user's password
  - `setIsAdmin()`: Updates admin status

### 2. AccessControl Class
- Manages a collection of users and handles authentication
- **Key Methods**:
  - `isValidLogin()`: Static method to validate username/password pairs
  - `addUser()`: Creates new users (admin-only)
  - `removeUser()`: Deletes users (admin-only)
  - `giveAdmin()/takeAdmin()`: Modifies admin privileges (admin-only)
  - `resetPassword()`: Resets password to default (admin-only)
  - `changePassword()`: Allows users to change their own password
  - `logout()`: Ends current user session

### 3. AccessControlTester Class
- Comprehensive test suite for the system
- **Test Methods**:
  - `testUserConstructorAndMethods()`: Tests User class functionality
  - `testAccessControlIsValidLoginNotValidUser()`: Tests login validation
  - `testAddUserWithNoAdminPowers()`: Tests permission enforcement
  - `testAddRemoveUserWithAdminPowers()`: Tests admin operations
  - `runAllTests()`: Runs all test cases

## How to Use

1. **Initialization**:
   ```java
   AccessControl system = new AccessControl();
   ```

2. **Admin Operations** (must be logged in as admin):
   ```java
   system.setCurrentUser("admin"); // Default admin user
   system.addUser("newuser"); // Add regular user
   system.addUser("newadmin", true); // Add admin user
   system.removeUser("olduser");
   ```

3. **User Operations**:
   ```java
   system.setCurrentUser("regularuser");
   system.changePassword("newsecurepassword");
   system.logout();
   ```

4. **Authentication**:
   ```java
   if (AccessControl.isValidLogin(username, password)) {
       // Valid credentials
   }
   ```

## Testing

Run all test cases with:
```java
AccessControlTester.runAllTests();
```

## Key Features

- Role-based access control (admin vs regular users)
- Secure password management
- Input validation
- Comprehensive test coverage
- Default admin account ("admin" with password "root")

## Requirements

- Java 8 or higher

## Notes

- Default password for new users: "changeme"
- Usernames must be at least 5 characters long
- All admin operations require current user to have admin privileges
