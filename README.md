# JSON API

1. Install dependencies.
   ```shell
   $ npm install
   ```
2. Start server.
   ```shell
   $ npm run start
   ```

Get a REST API for logs with filteration, sorting and pagination.

```shell
$ curl http://localhost:3000/logs/2
{
  "id": "2",
  "action": "Activity Clicked",
  "status": "Clicked",
  "details": "Conditaion Page with #checkbox Clicked",
  "user_id": "421011111",
  "timestamp": "2024-08-12 20:08:48.860000"
}
```

## Routes

Based on the example `db.json`, you'll get the following routes:

```
GET    /logs
GET    /logs/:id
POST   /logs
PUT    /logs/:id
PATCH  /logs/:id
DELETE /logs/:id

```

## Params

### Conditions

- ` ` → `==`
- `lt` → `<`
- `lte` → `<=`
- `gt` → `>`
- `gte` → `>=`
- `ne` → `!=`

```

GET /logs?views_gt=9000

```

### Range

- `start`
- `end`
- `limit`

```

GET /logs?\_start=10&\_end=20
GET /logs?\_start=10&\_limit=10

```

### Paginate

- `page`
- `per_page` (default = 10)

```

GET /logs?\_page=1&\_per_page=25

```

### Sort

- `_sort=f1,f2`

```

GET /logs?\_sort=id,-views

```

### Nested and array fields

- `x.y.z...`
- `x.y.z[i]...`

```

GET /foo?a.b=bar
GET /foo?x.y_lt=100
GET /foo?arr[0]=bar

```

## Delete

```

DELETE /logs/1

```

### Few Examples:

1. http://localhost:3000/logs/
2. http://localhost:3000/logs?\_page=2&\_per_page=2
3. http://localhost:3000/logs/3
4. http://localhost:3000/logs?\_sort=status
5. http://localhost:3000/products?\_sort=-stock
6. http://localhost:3000/orders/4
