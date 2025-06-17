# Airbnb Clone Project

## 📌 Overview

The Airbnb Clone Project is a comprehensive full-stack web development project that aims to replicate the core features of Airbnb. This includes user authentication, property listings, booking functionality, and more. It is designed to simulate a real-world development experience, emphasizing collaboration, scalability, and clean code architecture.

## 🎯 Project Goals

- Build a scalable, real-world Airbnb-like platform.
- Gain hands-on experience with both backend and frontend technologies.
- Practice collaborative software development using Git and GitHub.
- Understand API design, database modeling, and deployment processes.

## 🛠️ Tech Stack

- **Frontend:** HTML, CSS, JavaScript (with a frontend framework if needed)
- **Backend:** Python, Flask or Django
- **Database:** MySQL or PostgreSQL
- **Version Control:** Git & GitHub
- **Deployment:** Heroku, Render, or any cloud platform

## 📂 Repository Structure (Planned)

---
## 👥 Team Roles

In this project, each team member plays a critical role in bringing the Airbnb Clone to life. Below are the key roles and their responsibilities:

### 🔧 Backend Developer
Responsible for building and maintaining the server-side logic of the application. This includes creating APIs, handling business logic, integrating databases, and ensuring data flows efficiently between the client and server.

### 🗄️ Database Administrator (DBA)
Manages the database structure and performance. Responsible for designing schemas, writing complex queries, optimizing database operations, performing backups, and ensuring data integrity and security.

### 🎨 Frontend Developer
Focuses on the user interface and experience. Converts design mockups into functional web pages using HTML, CSS, and JavaScript. Ensures responsiveness, accessibility, and seamless user interactions.

### 🧪 QA Engineer (Quality Assurance)
Ensures that the application functions correctly through manual and automated testing. Responsible for finding bugs, writing test cases, and validating new features before deployment.

### 📦 DevOps Engineer
Manages the infrastructure and deployment pipeline. Sets up CI/CD, monitors system performance, handles scaling, and ensures that the application is always available and running smoothly.

### 📋 Project Manager
Coordinates the team, manages timelines, and ensures milestones are met. Acts as the liaison between stakeholders and developers, ensuring alignment with project goals and deadlines.

### 🎯 Product Owner
Defines the product vision and priorities. Gathers requirements, maintains the product backlog, and ensures that the development team delivers value that meets user needs.

---

Each team member contributes to the success of the Airbnb Clone Project by collaborating closely and aligning their efforts with the overall goals and technical vision.

---
## 🧰 Technology Stack

The Airbnb Clone Project is built using a modern technology stack that ensures scalability, performance, and maintainability.

- **Django**: A high-level Python web framework used for building the RESTful API, handling routing, models, and core backend logic.

- **Django REST Framework (DRF)**: An extension of Django that provides powerful tools and libraries for building and managing RESTful APIs with ease and flexibility.

- **PostgreSQL**: A robust, open-source relational database system used to store and manage structured data such as user information, property listings, and bookings.

- **GraphQL**: A query language that allows clients to request only the data they need, improving efficiency and flexibility in data fetching.

- **Celery**: A distributed task queue used to handle background and asynchronous operations like sending notifications or processing payments.

- **Redis**: An in-memory data store used for caching, task queuing with Celery, and session management to enhance performance.

- **Docker**: A containerization platform that ensures consistent development, testing, and production environments by packaging the application and its dependencies.

- **CI/CD Pipelines**: Continuous Integration and Continuous Deployment tools automate the process of testing, building, and deploying code changes, ensuring reliability and faster delivery.


## 🗃️ Database Design

This Airbnb Clone project uses a relational database to represent the key components of a booking platform. Below are the core entities, their fields, and how they relate to each other.

### 1. Users
Represents all users on the platform — guests and hosts.

- `id` (Primary Key)
- `full_name`
- `email` (Unique)
- `password_hash`
- `phone_number`
- `is_host` (Boolean)

**Relationships**:
- A user can own multiple properties (if they are a host).
- A user can make multiple bookings (as a guest).
- A user can write reviews for properties and hosts.

---

### 2. Properties
Represents a home or apartment listed by a host.

- `id` (Primary Key)
- `host_id` (Foreign Key to Users)
- `title`
- `description`
- `address`
- `city`
- `state`
- `country`
- `price_per_night`
- `property_type` (e.g., apartment, house)
- `max_guests`
- `created_at`

**Relationships**:
- A property belongs to one host (User).
- A property can have many bookings.
- A property can have many reviews.
- A property can have multiple images.

---

### 3. Bookings
Represents a reservation made by a guest for a property.

- `id` (Primary Key)
- `guest_id` (Foreign Key to Users)
- `property_id` (Foreign Key to Properties)
- `start_date`
- `end_date`
- `guests_count`
- `total_price`
- `status` (e.g., pending, confirmed, canceled)

**Relationships**:
- A booking is made by one guest for one property.
- A booking has one payment transaction.

---

### 4. Reviews
Represents feedback left by a guest after their stay.

- `id` (Primary Key)
- `guest_id` (Foreign Key to Users)
- `property_id` (Foreign Key to Properties)
- `rating` (1–5)
- `comment`
- `created_at`

**Relationships**:
- A review belongs to one guest and one property.
- A property can have many reviews.

---

### 5. Payments
Handles transactions for bookings.

- `id` (Primary Key)
- `booking_id` (Foreign Key to Bookings)
- `amount`
- `payment_method` (e.g., credit card, PayPal)
- `payment_date`
- `status` (e.g., paid, failed)

**Relationships**:
- A payment belongs to one booking.

---

### 6. PropertyImages
Stores URLs or file paths of property images.

- `id` (Primary Key)
- `property_id` (Foreign Key to Properties)
- `image_url`
- `is_primary` (Boolean)

**Relationships**:
- A property can have many images.

---

### 🔗 Entity Relationships Summary

- A **User**:
  - Can be a **Host** (owns properties) or a **Guest** (makes bookings).
  - Can write reviews.
- A **Property**:
  - Belongs to one **Host**.
  - Can have many **Bookings**, **Reviews**, and **Images**.
- A **Booking**:
  - Is made by a **Guest** for a **Property**.
  - Has one **Payment**.
- A **Review**:
  - Is written by a **Guest** for a **Property**.
- A **Payment**:
  - Is tied to one **Booking**.
- A **PropertyImage**:
  - Belongs to a **Property**.

