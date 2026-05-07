# FastAPI Dependency Injection

Dependency Injection (DI) is a core concept in FastAPI, making it extremely easy to manage dependencies like database connections, authentication, and configurations.

## Key Benefits
- **Shared Logic**: Write code once and reuse it across multiple endpoints.
- **Testing**: Easily mock dependencies during testing using `app.dependency_overrides`.
- **Database Connections**: Manage database sessions cleanly per request.

## Example: Database Session

```python
from fastapi import Depends, FastAPI
from sqlalchemy.orm import Session

app = FastAPI()

def get_db():
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()

@app.get("/users/")
def read_users(db: Session = Depends(get_db)):
    users = db.query(User).all()
    return users
```

In this example, `get_db` is injected into `read_users`. FastAPI automatically handles the lifecycle of the dependency, ensuring the database connection is closed after the request finishes.
