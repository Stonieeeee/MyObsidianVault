##### These are all query notes that I learned in Oracle Database.

"Find table names containing specific column name (header) and schema owner."

```sql
SELECT OWNER AS SchemaName, TABLE_NAME
FROM ALL_TAB_COLUMNS
WHERE OWNER = 'SPAPP' -- Note: Oracle names are usually uppercase
AND COLUMN_NAME = 'PROJ_CODE'
ORDER BY TABLE_NAME;
```



