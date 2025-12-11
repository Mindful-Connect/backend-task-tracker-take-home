# Backend Developer Take-Home Test: Task Tracker API

Thank you for your interest and for taking the time to complete our take-home test. This exercise is designed to assess your proficiency with the Laravel framework, your understanding of API design, and your general coding practices.

**Time Expectation:** This project should take approximately 2-4 hours. Please do not spend more than 4 hours on it. We are looking for your best work within that timeframe.

---

## Objective

You are tasked with building the backend API for a simple "Task Tracker" application. The application needs to manage **Projects** and their associated **Tasks**.

The core relationship is:
*   A **Project** can have many **Tasks**.
*   A **Task** must belong to a single **Project**.

### Entity Schemas

**Project:**
*   `id` (integer, auto-incrementing)
*   `name` (string, required)
*   `description` (text, nullable)

**Task:**
*   `id` (integer, auto-incrementing)
*   `project_id` (foreign key)
*   `title` (string, required)
*   `status` (string, defaults to 'pending')

---

## API Endpoints & Requirements

### 3.1 Project Endpoints

| Method | URI                      | Description                                                               | Validation / Rules                                                               |
| :----- | :----------------------- | :------------------------------------------------------------------------ | :------------------------------------------------------------------------------- |
| `GET`  | `/api/projects`          | Fetch a paginated list of all projects.                                   |                                                                                  |
| `POST` | `/api/projects`          | Create a new project.                                                     | `name` is required and must be a string.                                         |
| `GET`  | `/api/projects/{project}`| Fetch a single project, including a list of its tasks.                    |                                                                                  |
| `PUT`  | `/api/projects/{project}`| Update an existing project's details.                                     | `name` is required and must be a string.                                         |
| `DELETE`| `/api/projects/{project}`| Delete a project. **Important**: Deleting a project should also delete all of its associated tasks. |                                                                                  |

### 3.2 Task Endpoints

| Method | URI                           | Description                               | Validation / Rules                                                                    |
| :----- | :---------------------------- | :---------------------------------------- | :------------------------------------------------------------------------------------ |
| `POST` | `/api/projects/{project}/tasks` | Create a new task for a given project.    | `title` is required. `status` should default to 'pending' if not provided.            |
| `PUT`  | `/api/tasks/{task}`           | Update an existing task's details.        | `title` is required. `status`, if provided, must be one of: `pending`, `in_progress`, `completed`. |
| `DELETE`| `/api/tasks/{task}`           | Delete a task.                            |                                                                                       |


### Technical Expectations

*   Use **Eloquent Models** and **Migrations** to set up the database schema and relationships.
*   Use **API Controllers** to handle the logic for each endpoint.
*   Use Laravel's built-in **Validation** (preferably via Form Requests) to validate incoming data.
*   Use **API Resources** to format the JSON output for your models.
*   Ensure your API returns appropriate HTTP status codes and a consistent JSON error format for validation failures.

---

## Getting Started

To ensure a smooth start, this project is pre-configured to use SQLite.

1.  From the GitHub page of this template, click **"Use this template"** > **"Create a new repository"**. Make your new repository **private**.
2.  Clone your new repository to your local machine.
3.  Run `cp .env.example .env`.
4.  Create an empty SQLite database file:
    *   *Mac/Linux:*
        ```bash
        touch database/database.sqlite
        ```
    *   *Windows:* Manually create an empty file named `database.sqlite` inside the `database` folder.
      
5.  Install PHP dependencies:
    ```bash
    composer install
    ```
6.  Generate an application key:
    ```bash
    php artisan key:generate
    ```
7.  Run the database migrations (once you've created them):
    ```bash
    php artisan migrate
    ```
8.  Start the local development server:
    ```bash
    php artisan serve
    ```

## Submission Process

1.  Once you are finished, ensure all your code is pushed to your private GitHub repository.
2.  Invite `Nuccino92` and `inflex13` as a collaborator to your private repository. (Go to `Settings` > `Collaborators` > `Add people`).
3.  Reply to our email with the link to your repository.

Good luck! We look forward to seeing your work.
