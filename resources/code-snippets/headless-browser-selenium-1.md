# Connect to a Postgres Database

Wayscript can programmatically connect to databases, including Postgres.&#x20;

### Install psycopg2 as a Package

Type the following two commands into your WayScript Terminal

```
pip install psycopg2-binary
pip freeze > requirements.txt
```

### Add your database credentials to your .secrets file

```bash
DB_HOST=my_database.example.com
DB_USERNAME=my_username
DB_PASSWORD=my_password
```

### Python

```python
import psycopg2
import os

# connect to a postgres database and execute SQL
# docs for psycopg2 library located  https://www.psycopg.org/docs/usage.html

# fetch database secrets from .secrets file
DBNAME="postgres"
PASSWORD= os.getenv("DB_PASSWORD")
USERNAME= os.getenv("DB_USERNAME")
DB_HOST = os.getenv("DB_HOST")

print("connecting to database...")
conn = psycopg2.connect(f"dbname={DBNAME} user={USERNAME} password={PASSWORD} host={DB_HOST}")
cur = conn.cursor()

print("creating table if it doesn't already exist...")
cur.execute("""
    CREATE TABLE IF NOT EXISTS users (
        id  SERIAL PRIMARY KEY,
        name varchar(45) NOT NULL,
        email varchar(80) NOT NULL,
        age INTEGER NOT NULL
    );
    """
)

# see https://www.psycopg.org/docs/usage.html#passing-parameters-to-sql-queries
print('inserting into users table...')
cur.execute("""
    INSERT INTO users (name, email, age)
    VALUES (%s, %s, %s);
    """,
    ('Alice', 'alice@example.com', 25)
)

print('committing changes to database...')
conn.commit()

print('fetching users table...')
cur.execute("SELECT * FROM users;")
res = cur.fetchall()
print(res)

print('closing connection...')
cur.close()
conn.close()
```

{% hint style="info" %}
more information on the psycopg2 library can be found here [https://www.psycopg.org/docs/usage.html](https://www.psycopg.org/docs/usage.html)
{% endhint %}
