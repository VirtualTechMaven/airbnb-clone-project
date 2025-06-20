# airbnb-clone-project-backend

## Team Roles

- **Backend Developer**: Builds and manages the API endpoints and business logic that power the platform. Responsible for handling user interactions, bookings, and data flow between the frontend and backend.

- **Database Administrator**: Designs, manages, and optimizes the database structure. Ensures data is stored securely and retrieved efficiently.

- **DevOps Engineer**: Manages deployment pipelines, infrastructure, and server maintenance. Ensures the system runs smoothly in all environments (dev, staging, production).

- **QA Engineer**: Writes test cases, tests the application for bugs, and ensures quality standards are met across features.

- **Project Manager** *(if included)*: Oversees the project timeline, communication between teams, and ensures milestones are met.

## Technology Stack

- **Django**: A high-level Python web framework used to build the main application and handle APIs.
- **Django REST Framework**: Adds tools for building RESTful APIs (e.g. `/users/`, `/bookings/`).
- **PostgreSQL**: A relational database used for storing user, property, booking, and review data.
- **GraphQL**: A query language used to fetch exactly the data we need in a flexible way.
- **Celery**: Handles background tasks like sending emails or payment processing.
- **Redis**: Used as a cache and message broker for Celery to improve performance.
- **Docker**: Packages the application so it can run in any environment.
- **CI/CD Tools (GitHub Actions)**: Automatically test and deploy code changes.

## Database Design

### Key Entities

- **User**
  - id
  - username
  - email
  - password
  - is_host (boolean)

- **Property**
  - id
  - name
  - description
  - price_per_night
  - host_id (FK → User)

- **Booking**
  - id
  - user_id (FK → User)
  - property_id (FK → Property)
  - check_in
  - check_out

- **Payment**
  - id
  - booking_id (FK → Booking)
  - amount
  - status
  - timestamp

- **Review**
  - id
  - user_id (FK → User)
  - property_id (FK → Property)
  - rating
  - comment

### Relationships

- A **User** can own many **Properties**.
- A **Booking** belongs to one **User** and one **Property**.
- A **Payment** is tied to one **Booking**.
- A **Review** is written by a **User** about a **Property**.

## Feature Breakdown

- **User Management**: Allows users to register, log in, update profiles, and become hosts.

- **Property Management**: Hosts can list, edit, and delete their rental properties, including pricing and availability.

- **Booking System**: Users can view properties, book available ones, and manage their check-in/check-out dates.

- **Payment Processing**: Enables secure payments and handles the financial transactions between users and hosts.

- **Review System**: After a stay, users can leave reviews and ratings for properties to help others make informed decisions.

## API Security

- **Authentication**: Ensures only registered users can access protected endpoints.
- **Authorization**: Limits certain actions to specific roles (e.g. only hosts can list properties).
- **Rate Limiting**: Prevents abuse of the API by restricting request frequency.
- **Data Validation**: Ensures incoming data is clean and prevents injection attacks.
- **HTTPS & Secure Headers**: Encrypts communication and protects from common vulnerabilities.

Security is critical for:
- Protecting user data (emails, payment info)
- Securing transactions (payments)
- Preventing misuse (like fake bookings or spam)

## CI/CD Pipeline

**CI/CD** stands for Continuous Integration and Continuous Deployment.

- **CI**: Automatically tests the code when you push to GitHub.
- **CD**: Automatically deploys the code if all tests pass.

### Tools we can use:
- **GitHub Actions**: For setting up test and deployment workflows.
- **Docker**: Ensures the app runs the same in dev and production.
- **Heroku / AWS / Render**: Can be used for automatic deployment.

