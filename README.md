<div align="center">

# Novera-Films
Practice Project... MongoDB,Express JS, Node JS
A movie discovery app built with **Node.js, Express, MongoDB, and Mongoose**.

[Getting Started](#getting-started) · [API](#api) · [Project Structure](#project-structure)

</div>

---

## About

Novera Films is a browsable movie catalog for discovering films to buy and watch. The Express API serves movie records stored in MongoDB, including descriptions, ratings, genres, artwork, and prices.

This project is also used to **practise Node.js, Express, MongoDB, and Mongoose** by building a working application from the ground up. It is a learning project, so the code and features will keep evolving as I learn.

## Features

- Featured movie carousel with automatic transitions and clickable slide controls
- Movie catalog populated from the API
- Movie details including description, rating, genre, runtime, director, and price
- REST-style endpoints for creating, reading, updating, and deleting movies
- Sorting, field selection, and pagination for catalog requests
- MongoDB-backed data models with validation
- Responsive layout for desktop and mobile screens

## Built With

- Node.js
- Express 5
- MongoDB and Mongoose
- HTML, CSS, and browser JavaScript

## Getting Started

### Prerequisites

- Node.js and npm
- A MongoDB database, local or hosted

### Install

```bash
git clone https://github.com/DenethPrabhashvara/Novera-Films
cd Novera-Films
npm install
```

Create a `config.env` file in the project root. Keep this file private and do not commit database credentials.

```env
DB_CONN_STRR=mongodb://127.0.0.1:27017/Novera_Films
```

For MongoDB Atlas, use your own Atlas connection string in `DB_CONN_STRR`.

Start the app:

```bash
npm start
```

Open (http://localhost:PORT) in your browser.

## API

All movie endpoints are mounted at `/movies`.

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/movies/` | Get a paginated list of movies |
| `POST` | `/movies/` | Create a movie from a JSON request body |
| `GET` | `/movies/:id` | Get a movie by MongoDB ID |
| `POST` | `/movies/:id` | Update a movie by ID |
| `DELETE` | `/movies/:id` | Delete a movie by ID |
| `GET` | `/movies/trending` | Get the trending movies at the time |

### Catalog Query Options

`GET /movies/` accepts these query parameters:

| Parameter | Example | Description |
|---|---|---|
| `page` | `?page=2` | Page number; defaults to `1` |
| `limit` | `?limit=20` | Results per page; defaults to `10` |
| `sortBy` | `?sortBy=rating,-releaseyear` | Sort fields; prefix a field with `-` for descending order |
| `fields` | `?fields=title,rating,price` | Select comma-separated fields |

Example:

```http
GET /movies/?page=1&limit=10&sortBy=-rating&fields=title,description,rating,price,coverImage
```

### Create a Movie

```http
POST /movies/
Content-Type: application/json
```

```json
{
  "title": "Example Film",
  "description": "A short description of the film.",
  "releaseyear": 2024,
  "rating": 8.2,
  "genres": ["Drama", "Mystery"],
  "runtime": 118,
  "director": "Example Director",
  "language": "English",
  "certificate": "PG-13",
  "coverImage": "https://example.com/poster.jpg",
  "price": 8.99
}
```

Movie titles are required and unique. Ratings must be between 1 and 10. The schema also requires a description, release year, genres, runtime, director, language, certificate, cover image, and price.

## Project Structure

```text
.
├── Controllers/       # Movie request handlers
├── Log/               # Application log output
├── Models/            # Mongoose movie schema
├── Utils/             # API query helper
├── routes/            # Movie API routes
├── app.js             # Express app and route mounting
├── server.js          # Environment, MongoDB connection, and server startup
├── index.html         # Novera Films home page
└── package.json       # Dependencies and npm scripts
```

## Learning in Progress

This is a hands-on practice project. Some implementation details are still being refined, and the test script is currently a placeholder. Feedback and suggestions are welcome as I continue improving the app.

---

<div align="center">

Made while learning Node.js and MongoDB.

</div>
