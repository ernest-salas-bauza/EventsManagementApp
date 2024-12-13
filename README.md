# Section 5: Project #3 - Events Management App (REST API)

This project is part of **Section 5** of the course, focusing on building a **RESTful API** for an **Event Management Application** using **Laravel 11**. The goal of this project is to create a fully functional API that can handle the creation, management, and deletion of events, along with the ability to register attendees, and manage their data.

## Features

- **Authentication & Authorization**: Users can register, log in, and manage events. Authorization is handled using **Laravel Sanctum** for token-based authentication.
- **Event Management**: Allows users to create, read, update, and delete events.
- **Attendee Management**: Users can add and remove attendees for specific events.
- **Rate Limiting**: Implemented rate limiting using Laravel’s built-in tools to control the number of requests a user can make in a given time period.
- **Validation**: Input validation is implemented for creating and updating events and attendees, ensuring that the data is correctly formatted.
- **CRUD Operations**: The app allows performing Create, Read, Update, and Delete operations for events and attendees using a RESTful approach.
- **Throttling & Rate Limiting**: Ensures the API is protected from abuse by limiting the number of requests a user can make per minute.

## Tools and Technologies

- **Laravel 11**: The PHP framework used to build the API.
- **Sanctum**: For API token authentication.
- **Rate Limiting**: Using Laravel’s `RateLimiter` for controlling API usage.
- **MySQL**: Database used to store event and attendee data.
- **Postman**: For testing and interacting with the API endpoints.

## Installation

### Prerequisites

Before running this application, make sure you have the following installed:
- **PHP 8.x** or above
- **Composer**
- **MySQL** or another database
- **Laravel 11** 
- **Postman** 

## **Setup Instructions**
1. Clone the repository:
   ```bash
   git clone https://github.com/ernest-salas-bauza/EventsManagementApp.git 
   ```
2. Install dependencies:
   ```bash
   composer install
   ```
3. Set up the `.env` file for database configuration and generate the application key:
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```
4. Run migrations to create database tables:
   ```bash
   php artisan migrate --seed
   ```
5. Serve the application locally:
   ```bash
   php artisan serve
   ```
6. Access the application in your browser at `http://localhost:8000`.

## Endpoints

### Authentication
- **POST** `/api/login` - User login (Returns an API token).
- **POST** `/api/register` - User registration.

### Events
- **GET** `/api/events` - List all events.
- **GET** `/api/events/{id}` - Show a specific event.
- **POST** `/api/events` - Create a new event.
- **PUT** `/api/events/{id}` - Update an event.
- **DELETE** `/api/events/{id}` - Delete an event.

### Attendees
- **POST** `/api/events/{event_id}/attendees` - Add an attendee to an event.
- **DELETE** `/api/events/{event_id}/attendees/{attendee_id}` - Remove an attendee from an event.

### Rate Limiting
The API uses rate limiting to restrict users to a set number of requests per minute. By default, each user is allowed **60 requests per minute**. You can adjust this limit in `AppServiceProvider.php`.

### Testing with Postman
You can test the API using Postman. Import the Postman collection available in the repository to get started with testing all the endpoints.

