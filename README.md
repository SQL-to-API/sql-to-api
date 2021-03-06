# sql-to-api

SQL to API idea is to set convention that enables using SQL to query API for data. SQL is converted to API call in client side. Examples in this document use JavaScript and fetch to describe different approaches.

`SELECT * FROM users` => `fetch('/api/users')`

`SELECT * FROM users WHERE name=Jack` => `fetch('/api/users?name=Jack')`

`SELECT * FROM users WHERE name=Jack ORDER BY age` => `fetch('/api/users?name=Jack').sort((userA,userB) => userA.age-userB.age)`


`SELECT * FROM Orders INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;` => `fetch.all([fetch('/api/orders'),[fetch('/api/customers')]).then((orders,customers)=>{ 
  return orders.filter(order=>{
    customers.filter(customer=>{
      if(customer.CustomerID === order.CustomerID){
        return true;
      }
      return false;
    });
  });
});` anyway join clause and inner braces mean another fetch
or https://stackoverflow.com/questions/6324547/how-to-handle-many-to-many-relationships-in-a-restful-api
or even better https://stackoverflow.com/questions/46581937/restful-api-with-relationships

# Code Structure

- Converter is Singleton
- Converter is configured through "configure(settings)" method where settings parameter is JSON
- Converter converts given sql to client syntax through "convertSQLToYourProgrammingLanguage(sql)"

# existing API design guidelines

https://cloud.google.com/apis/design/
https://blinkboxbooks.github.io/2014/11/18/restful-api-design-guidelines.html
https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api

MS API design guideline 
https://github.com/Microsoft/api-guidelines/blob/vNext/Guidelines.md
is not REST...
https://www.infoq.com/news/2016/07/microsoft-rest-api/
