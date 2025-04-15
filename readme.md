# 🧪 FastAPI Test Suite — Final Submission

This repository contains a FastAPI application tested with **Pytest**, **HTTPX**, and **SQLAlchemy**, built with support for JWT-based authentication, role-based access control, and mocked services like email sending.

## ✅ GitHub Issues and Fixes

Below are five closed issues that demonstrate debugging, validation, and workflow improvements. Each issue is linked and includes the relevant code fixes:

1. [#1  - Test test_user_schema: fixed first name, nickname errors](https://github.com/mb2362/event_manager/issues/1)
2. [#2  - Test USER,LOGIN : VALIDATION ERROR](https://github.com/mb2362/event_manager/issues/2)
3. [#3  - [Bug] Workflow doesn't run on push](https://github.com/mb2362/event_manager/issues/3)
4. [#6  - [Bug] Missing user_token fixture in test setup causes test failure](https://github.com/mb2362/event_manager/issues/6)
5. [#8  - [Bug] Missing admin_token fixture breaks admin-auth tests](https://github.com/mb2362/event_manager/issues/8)
6. [#10 - [Bug] Missing manager_token fixture prevents manager-auth test execution](https://github.com/mb2362/event_manager/issues/10)
7. [#12 - OpenAPI Docs page login and register example data mismatch](https://github.com/mb2362/event_manager/issues/12)

All issues are merged into the `main` branch and tracked through descriptive commits and pull requests, following Git best practices.

## 🐳 DockerHub Deployment

View the deployed image on DockerHub:
👉 [DockerHub - monilbaxi/myfastapi](https://hub.docker.com/layers/monilbaxi/myfastapi/latest/images/sha256:84b44e748593b16a7564cb8f4b16358da1b046c2b6e9c021de478751bf9b31bd?uuid=89510C6A-9DEA-45D4-931B-36ADA179C6E8)

## 🫚an Updated Example Fixtures

```python
@pytest.fixture
def user_response_data():
    return {
        "id": uuid4(),
        "username": "testuser",
        "email": "test@example.com",
        "last_login_at": datetime.now(),
        "created_at": datetime.now(),
        "updated_at": datetime.now(),
        "links": [{"rel": "self", "href": "/users/testuser"}]
    }

@pytest.fixture
def login_request_data():
    return {"email": "john.doe@example.com", "password": "SecurePassword123!"}

@pytest.fixture
def user_base_data_invalid():
    return {
        "username": "john_doe_123",
        "email": "john.doe.example.com",
        "full_name": "John Doe",
        "bio": "I am a software engineer with over 5 years of experience.",
        "profile_picture_url": "https://example.com/profile_pictures/john_doe.jpg"
    }

@pytest.fixture
def user_create_data(user_base_data):
    return {**user_base_data, "password": "SecurePassword123!"}

@pytest.fixture
def user_update_data():
    return {
        "email": "john.doe.new@example.com",
        "full_name": "John H. Doe",
        "bio": "I specialize in backend development with Python and Node.js.",
        "profile_picture_url": "https://example.com/profile_pictures/john_doe_updated.jpg",
        "nickname": "manager_john",
        "first_name": "John",
    }
```

## 📚 Reflection

This assignment provided valuable hands-on experience in writing and managing test suites for asynchronous FastAPI applications. I learned how to design reusable fixtures with pytest, manage dependencies between services using mocking techniques like AsyncMock, and ensure schema correctness through real-world test scenarios. Fixing schema validation errors taught me to align test data precisely with Pydantic expectations, and I now appreciate how even small field mismatches can cause cascading failures.

On the collaboration side, using GitHub Issues and Pull Requests helped structure the debugging process and track changes meaningfully. I also learned how to automate workflows with GitHub Actions and maintain a clean main branch using feature branches. Reflecting on my development process and writing documentation made it easier to identify what worked well and where improvements could be made. This holistic approach combining testing, debugging, and workflow automation will be highly useful in both individual and team projects going forward.

## 💻 Environment

| Tool              | Version         |
|-------------------|------------------|
| OS                | Ubuntu 22.04     |
| Python            | 3.10.12          |
| Pytest            | 8.1.1            |
| FastAPI           | 0.110.0          |
| SQLAlchemy        | 2.0.29           |
| httpx             | 0.27.0           |
| pytest-asyncio    | 0.23.6           |
| alembic           | 1.13.1           |
| uvicorn           | 0.29.0           |
| bcrypt            | 4.1.2            |
| email-validator   | 2.1.1            |
| python-jose       | 3.3.0            |
| asyncpg           | 0.29.0           |
| aiomysql          | 0.2.0            |
| PyMySQL           | 1.1.0            |
| gunicorn          | 21.2.0           |
| coverage          | 7.4.4            |
| factory-boy       | 3.3.0            |
| Faker             | 24.4.0           |

## 📬 Contact

For issues, suggestions, or contributions, feel free to open an [Issue](https://github.com/mb2362/event_manager/issues) or submit a PR.