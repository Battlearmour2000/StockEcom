# Django Stock E-commerce API

A Django REST Framework API for managing stock and e-commerce functionality.

## 🐳 Docker Deployment

This project can be easily deployed using Docker. Here's how to get started:

### Prerequisites

- [Docker](https://www.docker.com/get-started)

### Environment Setup

Before building the Docker image, create a `.env` file in the project root with these variables:

```
DB_NAME=your_db_name
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=your_db_host
DB_PORT=5432
```

### Quick Start with Docker

1. **Build the Docker Image**

   ```bash
   docker build -t stock-ecomm .
   ```

2. **Run the Container**

   ```bash
   docker run -d -p 8000:8000 --env-file .env --name stock-ecomm-container stock-ecomm
   ```

3. **Access the Application**
   The API will be available at `http://localhost:8000`

### 🔑 Superuser Setup

The Dockerfile automatically creates a default superuser with these credentials:

- Username: admin
- Email: admin@example.com
- Password: admin

To customize the superuser during build, use these build arguments:

```bash
docker build \
  --build-arg DJANGO_SUPERUSER_USERNAME=your_username \
  --build-arg DJANGO_SUPERUSER_EMAIL=your_email@example.com \
  --build-arg DJANGO_SUPERUSER_PASSWORD=your_password \
  -t stock-ecomm .
```

### 🔧 Docker Configuration

Our Dockerfile handles:

- Setting up Python 3.10 environment
- Installing PostgreSQL dependencies
- Installing project dependencies
- Running migrations automatically
- Collecting static files
- Creating a default superuser

You don't need to manually:

- Run migrations
- Collect static files
- Create a superuser

### 🚀 Useful Docker Commands

- **View logs:**

  ```bash
  docker logs stock-ecomm-container
  ```

- **Execute commands in the container:**

  ```bash
  docker exec -it stock-ecomm-container python manage.py command_name
  ```

- **Stop the container:**
  ```bash
  docker stop stock-ecomm-container
  ```

## 💻 Local Development Setup

If you prefer to run the application locally without Docker:

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Set up a virtual environment**

   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: env\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file as described in the Docker section.

5. **Run migrations**

   ```bash
   python manage.py migrate
   ```

6. **Create a superuser**

   ```bash
   python manage.py createsuperuser
   ```

7. **Start the development server**
   ```bash
   python manage.py runserver
   ```

## 📋 API Documentation

API documentation can be found at:

- Swagger UI: `/api/schema/swagger-ui/`
- ReDoc: `/api/schema/redoc/`

## 🤝 Contributing

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Submit a pull request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.
