# COALESCE

Owner: Edwin

```sql
SELECT name FROM Customer WHERE COALESCE(referee_id, 0) != 2;
```