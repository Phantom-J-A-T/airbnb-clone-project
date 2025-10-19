# Airbnb Clone Project

## 🏠 Overview
This project is a full-stack clone of Airbnb, designed to simulate the platform’s key features such as property listings, user authentication, booking management, and search filters. It serves as a learning project to practice modern web development techniques, API integration, and responsive design.

## 🎯 Project Goals
- Build a responsive, dynamic, and visually appealing web application.
- Implement authentication and authorization for users.
- Allow hosts to list properties and guests to book them.
- Integrate a database to manage user data, listings, and bookings.
- Deploy the app for public access.

## 🧰 Tech Stack
**Frontend:**
- React.js (with Next.js or Vite)
- Tailwind CSS for styling
- Axios for API requests

**Backend:**
- Node.js with Express.js
- MongoDB or PostgreSQL as the database
- JWT for authentication
- Cloudinary or AWS S3 for image uploads

**Deployment:**
- Frontend: Vercel or Netlify
- Backend: Render, Railway, or AWS

---

## 🚀 Getting Started
1. Clone the repo:
   ```bash
   git clone https://github.com/<your-username>/airbnb-clone-project.git

   ---

## 👥 Team Roles

Building the Airbnb Clone requires collaboration across several technical roles. Below are the key roles and their responsibilities, inspired by standard software development practices and the ITRex Group’s team structure.

### 🧑‍💻 Frontend Developer
Responsible for creating the user interface and ensuring a smooth, responsive user experience.  
- Builds reusable React components.
- Implements responsive layouts using Tailwind CSS.
- Integrates frontend with backend APIs.
- Ensures accessibility and performance optimization.

### ⚙️ Backend Developer
Handles server-side logic, APIs, and data flow between the frontend and the database.  
- Designs and implements RESTful APIs using Node.js and Express.
- Manages authentication and authorization (JWT, sessions).
- Integrates with cloud services (e.g., file storage, payment systems).
- Ensures backend scalability and security.

### 🗃️ Database Administrator (DBA)
Oversees the database structure, performance, and data integrity.  
- Designs database schema for users, listings, and bookings.
- Optimizes queries and manages indexing.
- Handles backup, replication, and recovery.
- Ensures data consistency and security.

### 🧠 UX/UI Designer
Focuses on the design and usability of the platform.  
- Creates wireframes and mockups for core pages.
- Defines color schemes, typography, and overall design language.
- Conducts usability testing to refine user experience.
- Collaborates with frontend developers to implement design systems.

### 🔐 DevOps Engineer
Ensures smooth deployment, integration, and maintenance of the application.  
- Automates builds, tests, and deployments using CI/CD pipelines.
- Manages environments (development, staging, production).
- Monitors performance and uptime.
- Implements security and scaling solutions.

### 🧭 Project Manager
Coordinates the entire project lifecycle and ensures timely delivery.  
- Defines milestones, tasks, and sprint goals.
- Facilitates communication between all team members.
- Tracks progress using Agile methodologies (Scrum/Kanban).
- Manages risk and scope changes effectively.

---


---

## 🧰 Technology Stack

Below are the core technologies used in the Airbnb Clone project, along with their specific purposes within the system architecture.

### 🖥️ Backend
- **Django:** A high-level Python web framework that simplifies building secure and maintainable web applications. It powers the backend logic and handles routing, authentication, and API endpoints.
- **Django REST Framework (DRF):** An extension of Django used to build RESTful APIs, allowing seamless communication between the frontend and backend.
- **GraphQL (via Graphene-Django):** Enables efficient and flexible data querying by allowing clients to request only the data they need.
- **PostgreSQL:** A robust relational database system used to store and manage user, listing, and booking data securely and efficiently.

### 💻 Frontend
- **React.js:** A powerful JavaScript library used to build a responsive, dynamic, and interactive user interface for the web app.
- **Next.js:** A React framework for server-side rendering and optimized page performance, improving SEO and load speed.
- **Tailwind CSS:** A utility-first CSS framework used to design sleek, modern, and fully responsive layouts.

### ☁️ DevOps & Deployment
- **Docker:** Used to containerize the application, ensuring consistency across development, testing, and production environments.
- **Nginx:** A high-performance web server that handles request routing and acts as a reverse proxy for the backend.
- **GitHub Actions:** Automates CI/CD pipelines for testing, building, and deploying the application.
- **AWS / Render / Vercel:** Cloud platforms for hosting both the backend and frontend, ensuring scalability and high availability.

### 🧪 Testing & Quality Assurance
- **Pytest:** Framework for testing Django and API logic to ensure code reliability.
- **Jest:** JavaScript testing framework used to test React components and frontend logic.
- **Postman:** API testing tool for verifying RESTful and GraphQL endpoints.

---

---

## 🗃️ Database Design

The Airbnb Clone project uses a **relational database model** (PostgreSQL) to store and manage structured data. The key entities and their relationships are designed to support user management, property listings, bookings, reviews, and payments.

### 🧑‍💼 1. Users
Represents all users of the platform — guests and hosts.
- **Fields:**
  - `id`: Unique identifier for each user.
  - `full_name`: The user's full name.
  - `email`: Unique email used for authentication.
  - `password_hash`: Securely stored hashed password.
  - `role`: Defines if the user is a guest, host, or admin.
- **Relationships:**
  - A user (host) can have multiple properties.
  - A user (guest) can make multiple bookings and leave reviews.

---

### 🏠 2. Properties
Represents rental listings created by hosts.
- **Fields:**
  - `id`: Unique property ID.
  - `title`: Name or short description of the listing.
  - `description`: Detailed information about the property.
  - `price_per_night`: Cost of one night’s stay.
  - `location`: City and country where the property is located.
- **Relationships:**
  - Each property belongs to one host (user).
  - A property can have multiple bookings and reviews.

---

### 📅 3. Bookings
Stores all booking transactions between guests and hosts.
- **Fields:**
  - `id`: Unique booking ID.
  - `check_in_date`: Start date of stay.
  - `check_out_date`: End date of stay.
  - `total_price`: Total cost for the stay duration.
  - `status`: Indicates if booking is pending, confirmed, or canceled.
- **Relationships:**
  - Each booking belongs to one user (guest) and one property.
  - A booking can have one related payment record.

---

### 💬 4. Reviews
Captures user feedback on properties after stays.
- **Fields:**
  - `id`: Unique review ID.
  - `rating`: Numeric score (1–5).
  - `comment`: Text review written by the guest.
  - `created_at`: Timestamp when the review was posted.
- **Relationships:**
  - Each review is written by one guest.
  - Each review belongs to one property.

---

### 💳 5. Payments
Tracks payment information for completed bookings.
- **Fields:**
  - `id`: Unique payment ID.
  - `booking_id`: Reference to the related booking.
  - `amount`: Amount paid.
  - `payment_method`: Payment type (credit card, PayPal, etc.).
  - `status`: Indicates if payment is successful, failed, or pending.
- **Relationships:**
  - Each payment is linked to a single booking.
  - A user can have multiple payments through different bookings.

---

### 🔗 Entity Relationships Summary
- **User ↔ Property:** One-to-Many (a host can own many properties).  
- **User ↔ Booking:** One-to-Many (a guest can make many bookings).  
- **Property ↔ Booking:** One-to-Many (a property can be booked many times).  
- **Property ↔ Review:** One-to-Many (a property can have many reviews).  
- **Booking ↔ Payment:** One-to-One (each booking has one payment record).

---




---

## ✨ Feature Breakdown

The Airbnb Clone project includes several core features that replicate real-world functionality from the Airbnb platform. Each feature is designed to enhance usability, scalability, and performance while offering a seamless user experience.

### 👤 User Management
Handles user registration, authentication, and profile management for both guests and hosts.  
Users can sign up, log in securely, update their profiles, and manage their bookings or listings depending on their role.

### 🏡 Property Management
Allows hosts to create, edit, and manage property listings.  
Hosts can upload images, set pricing, specify amenities, and define property availability, giving guests accurate information before booking.

### 📅 Booking System
Facilitates the entire booking process from property selection to confirmation.  
Guests can view available dates, make reservations, and track booking statuses, while hosts can approve or manage booking requests.

### 💳 Payment Integration
Enables guests to make secure payments for their bookings.  
Supports multiple payment methods (e.g., credit/debit cards, PayPal), with transaction tracking and confirmation for both guests and hosts.

### ⭐ Reviews & Ratings
Allows guests to leave feedback and rate their stay after a completed booking.  
These reviews help future guests make informed decisions and motivate hosts to maintain high-quality standards.

### 🔍 Advanced Search & Filters
Provides users with powerful search functionality to find properties based on criteria such as location, price range, amenities, and availability.  
This improves navigation efficiency and ensures users can quickly discover the most relevant listings.

### 📱 Responsive Design
Ensures the platform is fully optimized for desktop, tablet, and mobile devices.  
Using Tailwind CSS and React, the interface dynamically adapts to different screen sizes for a smooth browsing experience.

### 🛠️ Admin Dashboard
Offers administrative tools to manage users, listings, and transactions.  
Admins can oversee platform activity, handle reported issues, and ensure compliance with platform policies.

---
