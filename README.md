# sql-to-api

SQL to API idea is to set convention that enables using SQL to query API for data. SQL is converted to API call in client side. Examples in this document use JavaScript and fetch to describe different approaches.

`SELECT * FROM users` => `fetch('/api/users')`

`SELECT * FROM users WHERE name=Jack` => `fetch('/api/users&name=Jack')`

`SELECT * FROM users WHERE name=Jack ORDER BY age` => `fetch('/api/users&name=Jack').sort((userA,userB) => userA.age-userB.age)`


# Code Structure

- Converter is Singleton
- Converter is configured through "configure(settings)" method where settings parameter is JSON
- Converter converts given sql to client syntax through "convertSQLToYourProgrammingLanguage(sql)"

