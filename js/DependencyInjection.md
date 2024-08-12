Dependency Injection is a way of handling objects that are dependent on other objects.

```typescript
class DatabaseConnection {
  connect() {
    console.log("Connected to database");
  }
}

class PostsRouter {
  get() {
    const db = new DatabaseConnection();
    db.connect();
    console.log("Posts retrieved");
  }
}
const posts = new PostsRouter;
posts.get();
```
In the example above the posts router is dependent on the database connection.

BUT there is a problem here. Even though this solution works, it’s not flexible. The code is, as we say tightly coupled.

That’s when dependency injection comes in.

Dependency injection is basically nothing more than **passing an object into the constructor or setter of a class that depends on that object**.

```typescript
class SQLiteConnection {
  connect() {
    console.log("Connected to SQlite");
  }
}

class MySqlConnection {
  connect() {
    console.log("Connected to MySQL");
  }
}

class PostsRouter {
  constructor(connection) {
    this.connection = connection;
  }
  get() {
    this.connection.connect();
    console.log("Posts retrieved");
  }
}

const mySql = new MySqlConnection;
const sqlite = new SQLiteConnection;

const mysqlPosts = new PostsRouter(mySql);

const sqlitePosts = new PostsRouter(sqlite);

mysqlPosts.get();
sqlitePosts.get();
```