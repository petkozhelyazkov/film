# Movies & TV Shows Backend API

Backend API for the Movies and TV Shows application with authentication and user profiles.

## Features

- User registration and login
- JWT-based authentication
- User profiles
- Favorites list (save movies/TV shows)
- Watch later list (save movies/TV shows for later)

## Setup

1. Install dependencies:
```bash
npm install
```

2. Create a `.env` file in the `backend` directory:
```bash
# Create .env file manually or copy from .env.example
```

3. **IMPORTANT**: Add the following to your `.env` file (JWT_SECRET is REQUIRED):
```
PORT=3000
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
NODE_ENV=development
```

**⚠️ Note**: The server will NOT start without JWT_SECRET. Make sure to set a strong secret key!

4. Start the server:
```bash
npm start
```

For development with auto-reload:
```bash
npm run dev
```

## API Endpoints

### Authentication

#### Register
```
POST /api/auth/register
Body: {
  "email": "user@example.com",
  "password": "password123",
  "name": "User Name"
}
```

#### Login
```
POST /api/auth/login
Body: {
  "email": "user@example.com",
  "password": "password123"
}
```

### User Profile (Requires Authentication)

#### Get Profile
```
GET /api/user/profile
Headers: Authorization: Bearer <token>
```

#### Update Profile
```
PUT /api/user/profile
Headers: Authorization: Bearer <token>
Body: {
  "name": "New Name",
  "email": "newemail@example.com"
}
```

### Favorites (Requires Authentication)

#### Get Favorites
```
GET /api/user/favorites
Headers: Authorization: Bearer <token>
```

#### Add to Favorites
```
POST /api/user/favorites
Headers: Authorization: Bearer <token>
Body: {
  "movieId": "123",
  "type": "movie" // or "tv"
}
```

#### Remove from Favorites
```
DELETE /api/user/favorites
Headers: Authorization: Bearer <token>
Body: {
  "movieId": "123",
  "type": "movie" // or "tv"
}
```

### Watch Later (Requires Authentication)

#### Get Watch Later
```
GET /api/user/watch-later
Headers: Authorization: Bearer <token>
```

#### Add to Watch Later
```
POST /api/user/watch-later
Headers: Authorization: Bearer <token>
Body: {
  "movieId": "123",
  "type": "movie" // or "tv"
}
```

#### Remove from Watch Later
```
DELETE /api/user/watch-later
Headers: Authorization: Bearer <token>
Body: {
  "movieId": "123",
  "type": "movie" // or "tv"
}
```

## Data Storage

The backend uses JSON file-based storage in the `data/` directory. For production, consider using a proper database like MongoDB or PostgreSQL.

## Security Notes

- Passwords are hashed using bcrypt
- JWT tokens expire after 7 days
- Change the JWT_SECRET in production
- Use HTTPS in production

