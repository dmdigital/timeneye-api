# Users

### Status

Stable.


## GET /users

Returns the list of account users (admin and PMs only)

### Returns
* HTTP Code: 200 OK
* users (array)
	* id (int)
	* name (string)
	* email (string)
	* enabled (tinyint)
	* isAdmin (tinyint)
	* createProjects (tinyint)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
GET `https://track.timeneye.com/api/3/users`

API returns:

    {
    	"users":[
    		{
    			"id":"127",
    			"name":"jimmy@commper.com",
    			"enabled":1,
    			"isAdmin":1,
    			"createProjects":0
    		}
		]
	}
	

## POST /users

Creates a new user (admins only)

### Parameters (POST data)
* email (string)
* name (string)
* isAdmin (int)
* sendWelcomeEmail (int)

### Returns
* HTTP Code: 201 Created
* id (int)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted: you cannot create users
* 406 Duplicated

### Example
POST `https://track.timeneye.com/api/3/users/`
Post Data: email=debugger@timeneye.com

API returns:

    {
        "id":1014
    }


## GET /users/[ID]/

Returns a user's details. Admins only.

### Returns
* HTTP Code: 200 OK
* id (int)
* name (string)
* email (string)
* enabled (tinyint)
* isAdmin (tinyint)
* createProjects (tinyint)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
GET `https://track.timeneye.com/api/3/users/156/`

API returns:

    	{
			"id":"156",
			"name":"cippolo@ocoss.com",
			"email":"cippolo@ocoss.com",
			"enabled":"1",
			"isAdmin":"0",
			"createProjects":"0"
		}


## PUT /users/[ID]/

Updates a user (admins only).

### Parameters (POST data, all optional)
* name (string)
* email (string)
* isAdmin (tinyint)
* createProjects (tinyint)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 404 Not found
* 406 Duplicated

### Example
PUT `https://track.timeneye.com/api/3/users/1245/`
Post Data: name=Michael+Clayton


## DELETE /users/[ID]/

Deletes a user (admin only).

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
DELETE `https://track.timeneye.com/api/3/users/1245/`


## GET /users/[ID]/projects/

Returns a user's projects. Admins only.

### Returns
* HTTP Code: 200 OK
* tasks
	* id (int)
	* name (string)
	* isPM (tinyint)
	* budgetMinutes (int, PM only)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted


### Example
GET `https://track.timeneye.com/api/3/users/1323/projects/`

API returns:

    {
    	"projects":[
    		{
    			"id":"127",
    			"name":"My great project",
    			"isPM":1
    		}
    	]
    }
	

## POST /users/[ID]/projects/

Adds a user to a project. Only PM can call this API.

### Parameters (POST data)
* userId (int)
* isPM (tinyint, optional)
* budgetHours (int, optional)

### Returns
* HTTP Code: 201 Created
* id (int)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted: you cannot add users
* 406 Duplicated

### Example
POST `https://track.timeneye.com/api/3/projects/1245/users/`
Post Data: userId=1432


## PUT /users/[ID]/projects/[ID]/

Updates a user-project association.

### Parameters (POST data, all optional)
* budgetHours (int)
* isPM (tinyint)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
PUT `https://track.timeneye.com/api/3/users/1245/projects/5599/`
Post Data: budgetHours=23


## DELETE /users/[ID]/projects/[ID]/

Removes a user from a project.

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
DELETE `https://track.timeneye.com/api/3/users/1245/projects/6692/`