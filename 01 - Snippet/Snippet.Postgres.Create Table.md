# Create Table

Owner: Edwin

## Auto-increment primary key

```sql
CREATE TABLE users (
	id SERIAL PRIMARY KEY,
	username VARCHAR(50)
);
```

---

## Foreign key

```sql
CREATE TABLE photos (
 	id SERIAL PRIMARY KEY,
  url VARCHAR(200),
  user_id INTEGER REFERENCES users(id) 
 );
```

---

## Validation

```sql
CREATE TABLE orders (
	id           SERIAL       PRIMARY KEY,
	name         VARCHAR(40)  NOT NULL UNIQUE,
	create_at    TIMESTAMP    NOT NULL,
	est_delivery TIMESTAMP    NOT NULL,
	price        INTEGER      NOT NULL DEFAULT 999,
	CHECK(price > 0),
	CHECK (create_at < est_delivery)
)
```