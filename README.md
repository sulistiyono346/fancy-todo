


- ROUTES 

| Tables        | HTTP    | Description                                                    |
| ------------------|:-------:| :---------------------------------------------------------:|
| /register         | POST    | Register Up with new user                                  |
| /login            | POST    | Login in get acces token                                   |
| /validate         | GET     | validate user login                                        |
| /glogin           | POST    | Get a single user info (authenticated user)                |
| /users/:email     | GET     | GET a user with info (authenticated user)                  |
| /task/            | GET     | GET a Task with info (authenticated user)                  |
| /task/group/:id   | GET     | GET a spesific task group with info (authenticated user)   |
| /task/            | PUT     | Updated a task with info (authenticated user)              |
| /task/completed   | PUT     | Completed task a user with info (authenticated user)       |
| /task/            | POST    | Created a new task with info (authenticated user)          |
| /task/            | DELETE  | Deleted a tasl with info (authenticated user)              |
| /group/           | GET     | GET a group with info (authenticated user)                 |
| /group/:id        | GET     | GET a spesific group with info (authenticated user)        |
| /group/           | PUT     | Updated a group with info (authenticated user)             |
| /group/member/:id | PUT     | add a group member with info (authenticated user)          |
| /group/remove/:id | PUT     | remove group a member with info (authenticated user)       |
| /group/           | POST    | Created a new group with info (authenticated user)         |
| /group/           | DELETE  | Deleted a group with info (authenticated user)             |



REGISTER NEW USER:

- URL

    /register

- Method:

    GET

- URL Params
    none

    Required:

    first_name=[STRING],

    last_name=[STRING],

    username=[STRING],

    email=[STRING],

    password=[STRING],

    role=[STRING]

- Success Response:

    Code: 201

    Content: 
    {
    "id": [INTEGER],
    "name": "[STRING]",
    "email": "[STRING]",
    "password": "[STRING]",
    "img":[STRING],
    "register_by": "[STRING]"
}
    


- Error Response:
    code :400

    Content :
   {
    "name": "SequelizeValidationError",
    "errors": [
        {
            "message": "Error:[message]",
            "type": "Validation error",
            "path": "[PATH]",
            "value": "[VALUE]",
            "origin": "FUNCTION",
            "instance": {
                 "id": [INTEGER],
                 "name": "[STRING]",
                 "email": "[STRING]",
                 "password": "[STRING]",
                 "img":[STRING],
                 "register_by": "[STRING]"
            },
            "validatorKey": "[KEY]",
            "validatorName": null,
            "validatorArgs": [],
            "__raw": {}
        }
    ]
}

LOGIN USER:

- URL

    /login

- Method:

    POST

- URL Params
    none

    Required:

    username=[STRING],

    password=[STRING],


- Success Response:

    Code: 200

    Content: 
    
   {
    "token": "[VALUE]"
}

- Error Response:
    code :400

    Content :
    
   {
    "msg": "wrong email/password"
    }

SEARCH USER:

- URL

    /users/:email

- Method:

    GET

- URL Params
    none

    Required:

    param=[STRING],


- Success Response:

    Code: 200

    Content: 
    
    {
    "id": [INTEGER],
    "name": "[STRING]",
    }

- Error Response:
    code :400

    Content :
    
   {
    "msg": "user not found"
    }




GET TASK

- URL

    /task/:email

- Method:

    GET

- URL Params
    none

    Required:

    param=[STRING],


- Success Response:

    Code: 200

    Content: 
    
   [ {[OBJECT_TASK_VALUE]
    }]

- Error Response:
    code :400

    Content :
    
   {
   err
    }

CREATED TASK

- URL

    /users/:email

- Method:

    POST

- URL Params
    none

    Required:

    param=[STRING],


- Success Response:

    Code: 200

    Content: 
    
    {   completed: [BOLEAN],
        _id: [OBJECT_ID],
        title: [STRING],
        description: [STRING],
        createdAt: [INTEGER],
        latitude: [INTEGER],
        longitude: [INTEGER],
        due_date: [STRING],
        user_id: [OBJECT_ID]
    }

- Error Response:
    code :400

    Content :
   {
    "msg": "Due Date Cannot Before the Current Date, please try again !"
    }


UPDATED TASK

- URL

    /task/

- Method:

    PUT

- URL Params
    none

    Required:

    param=[STRING],


- Success Response:

    Code: 200

    Content: 
    
    {   completed: [BOLEAN],
        _id: [OBJECT_ID],
        title: [STRING],
        description: [STRING],
        createdAt: [INTEGER],
        latitude: [INTEGER],
        longitude: [INTEGER],
        due_date: [STRING],
        user_id: [OBJECT_ID]
    }

- Error Response:
    code :400

    Content :
   {
    "msg": "Due Date Cannot Before the Current Date, please try again !"
    }

COMPLETED TASK

- URL

    /task/completed

- Method:

    PUT

- URL Params
    none

    Required:

    body.id=[OBJECT_ID],


- Success Response:

    Code: 200

    Content: 
    
    {   completed: [BOLEAN],
        _id: [OBJECT_ID],
        title: [STRING],
        description: [STRING],
        createdAt: [INTEGER],
        latitude: [INTEGER],
        longitude: [INTEGER],
        due_date: [STRING],
        user_id: [OBJECT_ID]
    }

- Error Response:
    code :400

    Content :
   {
    err[err]
    }

DELETED TASK

- URL

    /task

- Method:

    DELETED

- URL Params
    none

    Required:

    body.id=[OBJECT_ID],


- Success Response:

    Code: 200

    Content: 
    
    {   result[data]
    }

- Error Response:
    code :400

    Content :
   {
    err[err]
    }

    




GET GROUP

- URL

    /group

- Method:

    GET

- URL Params
    none

    Required:

    param=[STRING],


- Success Response:

    Code: 200

    Content: 
    
    [ { members: [ [OBJECT] ],
        _id: [OBJECT_ID],
        title:[STRING],
        description: [STRING],
         } ]

- Error Response:
    code :400

    Content :
    
   {
    err[err]
    }

CREATED TASK

- URL

    /Groups

- Method:

    POST

- URL Params
    none

    Required:

    param=[STRING],


- Success Response:

    Code: 200

    Content: 
    
   { members:[OBJECT],
    _id: [OBJECT_ID],
    title: [STRING],
    description: [STRING],
    }

- Error Response:
    code :400

    Content :
   {
    err[err]
    }


UPDATED GROUP

- URL

    /group/

- Method:

    PUT

- URL Params
    none

    Required:

    param=[STRING],


- Success Response:

    Code: 200

    Content: 
    
   { members:[OBJECT],
    _id: [OBJECT_ID],
    title: [STRING],
    description: [STRING],
    }

- Error Response:
    code :400

    Content :
   {
   err[err]
    }

COMPLETED TASK

- URL

    /task/completed

- Method:

    PUT

- URL Params
    none

    Required:

    body.id=[OBJECT_ID],


- Success Response:

    Code: 200

    Content: 
    
    { members:[OBJECT],
    _id: [OBJECT_ID],
    title: [STRING],
    description: [STRING],
    }

- Error Response:
    code :400

    Content :
   {
    err[err]
    }

DELETED GROUP

- URL

    /group

- Method:

    DELETED

- URL Params
    none

    Required:

    body.id=[OBJECT_ID],


- Success Response:

    Code: 200

    Content: 
    
    {   result[data]
    }

- Error Response:
    code :400

    Content :
   {
    err[err]
    }

    

