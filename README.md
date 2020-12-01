# WHATABYTE Menu API

## API Endpoints

### 🔓 List Items

Lists all items from the menu.

```bash
GET /api/menu/items
```

#### Response

```bash
Status: 200 OK
```

```json
[
  {
    "id": 1,
    "name": "Burger",
    "price": 599,
    "description": "Tasty",
    "image": "https://cdn.auth0.com/blog/whatabyte/burger-sm.png"
  },
  {
    "id": 2,
    "name": "Pizza",
    "price": 299,
    "description": "Cheesy",
    "image": "https://cdn.auth0.com/blog/whatabyte/pizza-sm.png"
  },
  {
    "id": 3,
    "name": "Tea",
    "price": 199,
    "description": "Informative",
    "image": "https://cdn.auth0.com/blog/whatabyte/tea-sm.png"
  }
]
```

### 🔓 Get an item

Provides information an item from the menu.

```bash
GET /api/menu/items/:id
```

#### Response

##### If item is not found

```bash
Status: 404 Not Found
```

##### If item is found

```bash
Status: 200 OK
```

```json
{
  "id": 1,
  "name": "Burger",
  "price": 599,
  "description": "Tasty",
  "image": "https://cdn.auth0.com/blog/whatabyte/burger-sm.png"
}
```

> 🔐 Protected Endpoints: These endpoints require the request to include an access token issued by Auth0 in the authorization header.

### 🔐 Create an item for the authenticated user

Creates an item in the menu for the authenticated user.

```bash
POST /api/menu/items
```

#### Input

| Name          | Type     | Description                                |
| ------------- | :------- | :----------------------------------------- |
| `name`        | `string` | **Required**. The item's name              |
| `description` | `string` | **Required**. The item's description       |
| `price`       | `number` | **Required**. The item's price in cents.   |
| `image`       | `string` | **Required**. The URL of the item's image. |

##### Example

```json
{
  "name": "Salad",
  "price": 4.99,
  "description": "Fresh",
  "image": "https://cdn.auth0.com/blog/whatabyte/salad-sm.png"
}
```

#### Response

```bash
Status: 201 Created
```

```json
{
  "id": "QvcDfWMwg",
  "name": "Salad",
  "price": 4.99,
  "description": "Fresh",
  "image": "https://cdn.auth0.com/blog/whatabyte/salad-sm.png"
}
```

### 🔐 Update an item

Update an item from the menu.

```bash
PUT /api/menu/items/:id
```

#### Input

| Name          | Type     | Description                                |
| ------------- | :------- | :----------------------------------------- |
| `name`        | `string` | **Required**. The item's name              |
| `description` | `string` | **Required**. The item's description       |
| `price`       | `number` | **Required**. The item's price in cents.   |
| `image`       | `string` | **Required**. The URL of the item's image. |

If you only need to update some of the item properties, leave the other values as they are.

##### Example

Take the following item as an example:

```json
{
  "name": "Burger",
  "price": 599,
  "description": "Tasty",
  "image": "https://cdn.auth0.com/blog/whatabyte/burger-sm.png"
}
```

If you want to update the description only, you'll send a request body like the following:

```json
{
  "name": "Burger",
  "price": 599,
  "description": "Juicy",
  "image": "https://cdn.auth0.com/blog/whatabyte/burger-sm.png"
}
```

#### Response

##### If item is not found

```bash
Status: 404 Not Found
```

##### If item is found

```bash
Status: 200 OK
```

```bash
{
  "id": "zAvIQGhn$b",
  "name": "Burger",
  "price": 599,
  "description": "Juicy",
  "image": "https://cdn.auth0.com/blog/whatabyte/burger-sm.png"
}
```

### 🔐 Remove all items

Remove all items from the menu.

```bash
DELETE /api/menu/items
```

#### Response

```bash
Status: 204 No Content
```

### 🔐 Remove an item

Remove an item from the menu.

```
DELETE /api/menu/items/:id
```

#### Response

##### If item is not found

```bash
Status: 404 Not Found
```

##### If item is found

```bash
Status: 204 No Content
```

### 🔐 Reset the list

Reset the menu database to its default values.

```bash
GET /api/menu/reset
```

#### Response

```bash
Status: 200 OK
```

```json
[
  {
    "id": 1,
    "name": "Burger",
    "price": 599,
    "description": "Tasty",
    "image": "https://cdn.auth0.com/blog/whatabyte/burger-sm.png"
  },
  {
    "id": 2,
    "name": "Pizza",
    "price": 299,
    "description": "Cheesy",
    "image": "https://cdn.auth0.com/blog/whatabyte/pizza-sm.png"
  },
  {
    "id": 3,
    "name": "Tea",
    "price": 199,
    "description": "Informative",
    "image": "https://cdn.auth0.com/blog/whatabyte/tea-sm.png"
  }
]
```
