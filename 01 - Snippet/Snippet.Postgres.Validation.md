# Validation

Owner: Edwin

```sql
ALTER TABLE products
ALTER COLUMN price
SET NOT NULL;
```

```sql
ALTER TABLE products
ALTER COLUMN price
SET DEFAULT 999;
```

```sql
ALTER TABLE products
ADD UNIQUE(name, department);
```

```sql
ALTER TABLE products
ADD CHECK(price > 0);
```

```sql
-- remove unique
ALTER TABLE products
DROP CONSTRAINT products_name_key;
```