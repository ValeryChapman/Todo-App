## Contents
<<<<<<< HEAD
<<<<<<< HEAD
- [API Constitution](#api_constitution)
  - [Request-response scheme](#api_constitution_scheme)
  - [Errors list](#api_constitution_errors_list)
=======
=======
>>>>>>> ee872c5e837ee56e744788753490757d7d6273a8
- [Structures](#structures)
  - [test](#structures_test)
>>>>>>> ee872c5e837ee56e744788753490757d7d6273a8
- [Routes](#routes)
  - [Sign Up](#routes_sign_up)
  - [Sign In](#routes_sign_in)
  - [Get all lists](#routes_all_lists)
  - [Get a list by Id](#routes_list)
  - [Create a list](#routes_create_list)
  - [Edit a list](#routes_edit_list)
  - [Delete a list](#routes_delete_list)
  - [Get all items](#routes_all_items)
  - [Get an item by Id](#routes_item)
  - [Create an item](#routes_create_item)
  - [Edit an item](#routes_edit_item)
  - [Delete an item](#routes_delete_item)

## API Constitution <div id="api_constitution"></div>
### Request-response scheme <div id="api_constitution_scheme"></div>
#### Request
```json5
{} // dictionary, array, or other parameters of a request
```
#### Response
#### Success:
```json5
{
    "status": "OK", // status ok
    "data": {}  // dictionary, array, or other results of a operation
}
```
#### Error:
```json5
{
    "status": "ERR", // status error
    "error": {
        "code": 1, // error code
        "message": "" // description of the error
    }
}
```

### Errors list <div id="api_constitution_errors_list"></div>
- `1` - Some exception occured 
- `1000` - Route not found
- `2000` - Object creation error (invalid request data)
- `2010` - Validation failed (invalid request data)
- `2020` - Database error
- `2030` - Object not found
- `3000` - Invalid authorization token

## Routes <div id="routes"></div>

### Sign Up (👱) <div id="routes_sign_up"></div>
```
Method: POST
```
```
/auth/sign-up
```
#### Request data:
| Name | Type | Description | Example | Required |
|--|--|--|--|:--:|
| name | string | Name | Alex | + |
| username | string | Username | alex_porge | + |
| password | string | User password | qwerty | + |

#### Good response example:
```json5
{
    "id": 1,
}
```

### Sign In (👱) <div id="routes_sign_in"></div>
```
Method: POST
```
```
/auth/sign-in
```
#### Request data:
| Name | Type | Description | Example | Required |
|--|--|--|--|:--:|
| username | string | Username | alex_porge | + |
| password | string | User password | qwerty | + |

#### Good response example:
```json5
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2MjkxMDExNDAsImlhd..."
}
```




### Get all lists (🔒) <div id="routes_all_lists"></div>
```
Method: GET
```
```
Authorization: Bearer ...
```
```
/api/lists
```

#### Good response example:
```json5
{
    "data": [
        {
            "id": 1,
            "title": "Main goals",
            "description": "My main goals"
        }
    ]
}
```



### Get a list by Id (🔒) <div id="routes_list"></div>
```
Method: GET
```
```
Authorization: Bearer ...
```
```
/api/lists/:Id
```

#### Good response example:
```json5
{
    "title": "Main goals",
    "description": "My main goals"
}
```

### Create a list (🔒) <div id="routes_create_list"></div>
```
Method: POST
```
```
Authorization: Bearer ...
```
```
/api/lists
```

#### Request data:
| Name | Type | Description | Example | Required |
|--|--|--|--|:--:|
| title | string | List name | Main goals | + |
| description | string | List description | My main goals... | - |

#### Good response example:
```json5
{
    "id": 1
}
```

### Edit a list (🔒) <div id="routes_edit_list"></div>
```
Method: PUT
```
```
Authorization: Bearer ...
```
```
/api/lists/:Id
```

#### Request data:
| Name | Type | Description | Example | Required |
|--|--|--|--|:--:|
| title | string | List name | Main goals | - |
| description | string | List description | My main goals... | - |

#### Good response example:
```json5
{
    "status": "ok"
}
```


### Delete a list (🔒) <div id="routes_delete_list"></div>
```
Method: DELETE
```
```
Authorization: Bearer ...
```
```
/api/lists/:Id
```

#### Good response example:
```json5
{
    "status": "ok"
}
```

### Get all items (🔒) <div id="routes_all_items"></div>
```
Method: GET
```
```
Authorization: Bearer ...
```
```
/api/lists/:Id/items
```

#### Good response example:
```json5
[
    {
        "id": 1,
        "title": "Buy a car",
        "description": "McLaren P1",
        "done": true
    },
    {
        "id": 2,
        "title": "Build a house",
        "description": "",
        "done": false
    }
]
```



### Get an item by Id (🔒) <div id="routes_item"></div>
```
Method: GET
```
```
Authorization: Bearer ...
```
```
/api/items/:Id
```

#### Good response example:
```json5
{
    "id": 1,
    "title": "Buy a car",
    "description": "McLaren P1",
    "done": false
}
```

### Create an item (🔒) <div id="routes_create_item"></div>
```
Method: POST
```
```
Authorization: Bearer ...
```
```
/api/lists/:Id/items
```

#### Request data:
| Name | Type | Description | Example | Required |
|--|--|--|--|:--:|
| title | string | Item name | Buy a car | + |
| description | string | Item description | McLaren P1 | - |

#### Good response example:
```json5
{
    "id": 1
}
```

### Edit an item (🔒) <div id="routes_edit_item"></div>
```
Method: PUT
```
```
Authorization: Bearer ...
```
```
/api/items/:Id
```

#### Request data:
| Name | Type | Description | Example | Required |
|--|--|--|--|:--:|
| title | string | List name | Main goals | - |
| description | string | List description | My main goals... | - |
| done | bool | Is it done? | true | - |

#### Good response example:
```json5
{
    "status": "ok"
}
```

### Delete an item (🔒) <div id="routes_delete_item"></div>
```
Method: DELETE
```
```
Authorization: Bearer ...
```
```
/api/items/:Id
```

#### Good response example:
```json5
{
    "status": "ok"
}
```
