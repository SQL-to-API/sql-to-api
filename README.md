# sql-to-api

SQL to API idea is to set convention that enables using SQL to query API for data. SQL is converted to API call in client side. Examples in this document use JavaScript and fetch to describe different approaches.

`SELECT * FROM users` => `fetch('/api/users')`

`SELECT * FROM users WHERE name=Jack` => `fetch('/api/users&name=Jack')`

`SELECT * FROM users WHERE name=Jack ORDER BY age` => `fetch('/api/users&name=Jack').sort((userA,userB) => userA.age-userB.age)`

# existing API design guidelines

https://cloud.google.com/apis/design/
https://blinkboxbooks.github.io/2014/11/18/restful-api-design-guidelines.html
https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api

MS API design guideline 
https://github.com/Microsoft/api-guidelines/blob/vNext/Guidelines.md
is not REST...
https://www.infoq.com/news/2016/07/microsoft-rest-api/
