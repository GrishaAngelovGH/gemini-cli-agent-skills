# Example: User Authentication Feature

## Summary
The User Authentication feature handles secure login, session management, and password hashing. It ensures that only authorized users can access protected routes while maintaining persistent sessions via JWT.

## Architecture & Implementation
The system follows a middleware-based approach using Passport.js and JWT.

### Key Components
- `src/auth/auth.service.ts`: Core logic for validating users and generating tokens.
- `src/auth/jwt.strategy.ts`: Validates the JWT in the Authorization header.
- `src/models/user.model.ts`: Defines the schema and password hashing hooks (bcrypt).

### Logic Flow
1. **Request:** User sends credentials to `/api/auth/login`.
2. **Validation:** `AuthService.validateUser()` checks if the user exists and compares hashed passwords.
3. **Token Generation:** If valid, `AuthService.login()` generates a JWT containing the `userId`.
4. **Response:** The server returns the JWT to the client.

## Usage Example
```bash
# Login request
curl -X POST http://localhost:3000/api/auth/login \
     -H "Content-Type: application/json" \
     -d '{"email": "user@example.com", "password": "securepassword"}'
```
