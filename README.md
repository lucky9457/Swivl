# Travel Diary Platform Backend API

This repository contains the backend API for the Travel Diary Platform, allowing users to create, read, update, and delete travel diary entries.

## Setup Instructions

1. **Clone the repository:**

2. **Install dependencies:**



3. **Set up the MongoDB database:**
- Make sure MongoDB is installed and running on your system.
- Create a new database named `travel_diary_db`.

4. **Start the server:**

## API Endpoints

### Authentication

- **Register User**
- **URL:** `/auth/register`
- **Method:** `POST`
- **Body Parameters:**
 - `username` (string, required): Username of the user.
 - `email` (string, required): Email address of the user.
 - `password` (string, required): Password of the user.
- **Response:** 
 - Status: `201 Created`
 - Body: `{ "message": "User registered successfully" }`

- **Login User**
- **URL:** `/auth/login`
- **Method:** `POST`
- **Body Parameters:**
 - `email` (string, required): Email address of the user.
 - `password` (string, required): Password of the user.
- **Response:** 
 - Status: `200 OK`
 - Body: `{ "token": "<JWT_token>" }`

### Diary Entries

- **Create Diary Entry**
- **URL:** `/diaryEntries`
- **Method:** `POST`
- **Authorization:** Bearer Token (JWT)
- **Body Parameters:**
 - `title` (string, required): Title of the diary entry.
 - `description` (string, required): Description of the diary entry.
 - `location` (string, required): Location of the diary entry.
 - `photos` (array of strings, optional): Array of photo URLs.
- **Response:** 
 - Status: `201 Created`
 - Body: `{ "_id": "<diary_entry_id>", "title": "<title>", "description": "<description>", "location": "<location>", "photos": ["<photo_url1>", "<photo_url2>"], "user": "<user_id>", "date": "<date_created>" }`

- **Get All Diary Entries**
- **URL:** `/diaryEntries`
- **Method:** `GET`
- **Authorization:** Bearer Token (JWT)
- **Response:** 
 - Status: `200 OK`
 - Body: Array of diary entries.

- **Get Diary Entry by ID**
- **URL:** `/diaryEntries/:id`
- **Method:** `GET`
- **Authorization:** Bearer Token (JWT)
- **Response:** 
 - Status: `200 OK`
 - Body: Diary entry object.

- **Update Diary Entry**
- **URL:** `/diaryEntries/:id`
- **Method:** `PUT`
- **Authorization:** Bearer Token (JWT)
- **Body Parameters:** Same as create diary entry.
- **Response:** 
 - Status: `200 OK`
 - Body: Updated diary entry object.

- **Delete Diary Entry**
- **URL:** `/diaryEntries/:id`
- **Method:** `DELETE`
- **Authorization:** Bearer Token (JWT)
- **Response:** 
 - Status: `200 OK`
 - Body: `{ "message": "Diary entry deleted successfully" }`

## Error Handling

- Validation errors (e.g., missing fields, invalid email format) will return a `400 Bad Request` response.
- Unauthorized access will return a `401 Unauthorized` response.
- Not found errors will return a `404 Not Found` response.
- Internal server errors will return a `500 Internal Server Error` response.

