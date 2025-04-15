# 🧪 FastAPI Test Suite — Final Submission

This repository contains a FastAPI application tested with **Pytest**, **HTTPX**, and **SQLAlchemy**, built with support for JWT-based authentication, role-based access control, and mocked services like email sending.

Issue #12 focused on ensuring that example data on the OpenAPI Docs page matched for login and registration. This helped testers avoid confusion and copy-paste errors when trying out the API manually. It was resolved by updating the user routes to reflect consistent data, and the issue was closed via [#12](https://github.com/mb2362/event_manager/tree/12-openapi-docs-page-login-and-register-example-data-mismatch).

All issues are merged into the `main` branch and tracked through descriptive commits and pull requests, following Git best practices.


## 📚 Reflection

Through this assignment, I strengthened my understanding of FastAPI's modular structure and improved my comfort working with async testing tools such as HTTPX and pytest-asyncio. I became adept at managing user schemas, authentication logic, and data validation for real-world APIs. Handling multiple GitHub issues also helped solidify a practical Git workflow with feature branching, pull requests, and issue tracking.

One of the more subtle but important lessons came from improving developer experience — such as ensuring that OpenAPI example data aligns with test user credentials (#12). These small adjustments can significantly improve usability. Collaborating with mock services, and writing test fixtures to mirror realistic user states also helped me think more like a backend engineer in a production team setting.

## 💻 Environment

| Tool            | Version      |
| --------------- | ------------ |
| OS              | Ubuntu 22.04 |
| Python          | 3.10.12      |
| Pytest          | 8.1.1        |
| FastAPI         | 0.110.0      |
| SQLAlchemy      | 2.0.29       |
| httpx           | 0.27.0       |
| pytest-asyncio  | 0.23.6       |
| alembic         | 1.13.1       |
| uvicorn         | 0.29.0       |
| bcrypt          | 4.1.2        |
| email-validator | 2.1.1        |
| python-jose     | 3.3.0        |
| asyncpg         | 0.29.0       |
| aiomysql        | 0.2.0        |
| PyMySQL         | 1.1.0        |
| gunicorn        | 21.2.0       |
| coverage        | 7.4.4        |
| factory-boy     | 3.3.0        |
| Faker           | 24.4.0       |

## 📬 Contact

For issues, suggestions, or contributions, feel free to open an Issue or submit a PR.