# MajorProject

This project is a full-stack web application designed for managing online listings, complete with user authentication, review functionalities, and potentially location-based features using Mapbox. It is built using Node.js, Express.js as the web framework, and EJS for templating, integrating various essential middleware and database tools.

## Technologies Used

-   **Backend**: Node.js, Express.js
-   **Database**: MongoDB (via Mongoose ODM)
-   **Templating**: EJS (Embedded JavaScript)
-   **Authentication**: Passport.js (Local Strategy with Passport-Local-Mongoose for Mongoose integration)
-   **Cloud Storage**: Cloudinary (for image uploads, integrated with Multer and Multer-Storage-Cloudinary)
-   **Mapping**: Mapbox (using `@mapbox/mapbox-sdk`)
-   **Validation**: Joi
-   **Environment Variables**: Dotenv
-   **Session Management**: Express-Session, Connect-Mongo
-   **Flash Messages**: Connect-Flash
-   **HTTP Method Overrides**: Method-Override
-   **Image Processing**: Sharp

## Setup Instructions

To get this project up and running on your local machine, follow these steps:

### Prerequisites

Ensure you have the following installed:

-   **Node.js**: Version 20.18.0 or higher. You can download it from [nodejs.org](https://nodejs.org/).
-   **MongoDB**: Make sure MongoDB is installed and running on your system. You can download it from [mongodb.com](https://www.mongodb.com/try/download/community).
-   **Cloudinary Account**: Required for image storage. Sign up at [cloudinary.com](https://cloudinary.com/).
-   **Mapbox Account**: Required for map functionalities. Sign up at [mapbox.com](https://www.mapbox.com/).

### Installation

1.  **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd MajorProject
    ```

2.  **Install dependencies:**

    ```bash
    npm install
    ```

### Environment Variables

Create a `.env` file in the root directory of the project and add the following environment variables. Replace the placeholder values with your actual credentials:

```
PORT=3000
DB_URL=mongodb://127.0.0.1:27017/majorproject
SECRET=<your-session-secret>
CLOUDINARY_CLOUD_NAME=<your-cloudinary-cloud-name>
CLOUDINARY_API_KEY=<your-cloudinary-api-key>
CLOUDINARY_API_SECRET=<your-cloudinary-api-secret>
MAPBOX_TOKEN=<your-mapbox-access-token>
```

-   `PORT`: The port on which the server will run.
-   `DB_URL`: Your MongoDB connection string. For local development, `mongodb://127.0.0.1:27017/majorproject` is common.
-   `SECRET`: A strong, random string used to sign the session ID cookie. Keep this secure.
-   `CLOUDINARY_CLOUD_NAME`, `CLOUDINARY_API_KEY`, `CLOUDINARY_API_SECRET`: Your credentials from your Cloudinary account.
-   `MAPBOX_TOKEN`: Your public access token from your Mapbox account.

### Database Initialization (Optional)

If you want to populate your database with sample data, you can run the initialization script:

```bash
node init/index.js
```

### Running the Application

To start the development server, run:

```bash
npm start
```

The application should now be accessible at `http://localhost:3000` (or the port you specified in your `.env` file).

## Directory Overview

Here's a breakdown of the key directories and their contents:

-   `app.js`: The main entry point of the application, handling server setup, middleware, and routing.
-   `cloudConfig.js`: Configuration file for cloud-related services, potentially for image uploads or other cloud storage.
-   `controllers/`: Contains the logic for handling requests and interacting with models. Each file typically corresponds to a major resource.
    -   `listings.js`: Handles operations related to listings (e.g., creating, viewing, updating, deleting).
    -   `reviews.js`: Manages review-related operations.
    -   `users.js`: Deals with user authentication and profile management.
-   `init/`: Likely contains initialization scripts or data.
    -   `data.js`: Sample data or initial data for the application.
    -   `index.js`: Initialization script.
-   `middleware.js`: Custom middleware functions used across the application, such as authentication checks or error handling.
-   `models/`: Defines the Mongoose schemas and models for the application's data.
    -   `listing.js`: Defines the schema and model for listings.
    -   `review.js`: Defines the schema and model for reviews.
    -   `user.js`: Defines the schema and model for users (including authentication fields).
-   `public/`: Stores static assets served directly to the client.
    -   `css/`: Contains CSS stylesheets.
        -   `rating.css`: Styles specific to star ratings.
        -   `style.css`: General application styles.
    -   `js/`: Contains client-side JavaScript files.
        -   `map.js`: JavaScript for map integration (e.g., displaying listings on a map).
        -   `script.js`: General client-side scripts.
-   `routes/`: Defines the API endpoints and connects them to the appropriate controller functions.
    -   `listing.js`: Routes for listing-related operations.
    -   `review.js`: Routes for review-related operations.
    -   `user.js`: Routes for user authentication and profile.
-   `schema.js`: Contains Joi schemas for server-side input validation.
-   `utils/`: Utility functions and custom error classes.
    -   `ExpressError.js`: A custom error class for handling operational errors in Express.
    -   `wrapAsync.js`: A utility function to wrap async route handlers for error handling.
-   `views/`: Contains EJS template files for rendering dynamic content.
    -   `error.ejs`: Template for displaying error pages.
    -   `includes/`: Reusable EJS partials.
        -   `flash.ejs`: Displays flash messages (e.g., success or error notifications).
        -   `footer.ejs`: The application's footer.
        -   `navbar.ejs`: The application's navigation bar.
    -   `layouts/`
        -   `boilerplate.ejs`: The main layout template that other views extend.
    -   `listings/`: EJS templates specific to listings.
        -   `edit.ejs`: Form for editing an existing listing.
        -   `index.ejs`: Displays a list of all listings.
        -   `new.ejs`: Form for creating a new listing.
        -   `show.ejs`: Displays details of a single listing.
    -   `users/`: EJS templates for user authentication.
        -   `login.ejs`: User login form.
        -   `signup.ejs`: User registration form.
