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
	

## POST /projects

Creates a new project

### Parameters (POST data)
* name (string)

### Returns
* HTTP Code: 201 Created
* id (int)

### Errors
* 400 Bad Request: missing required parameters | Name is too short
* 401 Unauthorized: authToken not valid
* 403 Not permitted: you cannot create projects
* 406 Duplicated

### Example
GET `https://track.timeneye.com/api/3/projects/1245`
Post Data: name=My+Test+Project

API returns:

    {
        "id":1014
    }


## GET /projects/[ID]/

Returns project's details. Some details are shown only to PMs and admins.

### Returns
* HTTP Code: 200 OK
* id (int)
* name (string)
* isActive (tinyint)
* clientId (int, PMs only)
* clientName (string, PMs only)
* hourlyRate (decimal, PMs only)
* budgetMinutes (int, PMs only)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
GET `https://track.timeneye.com/api/3/projects/1323/`

API returns:

    {
        "id":"1014",
        "name":"Ciccio Pasticcio2",
        "isActive":"1",
        "clientId":"-1",
        "clientName":"",
        "isBillable":"0",
        "hourlyRate":"0.00",
        "budgetMinutes":"0"
	}


## PUT /projects/[ID]/

Updates a project (PMs only).

### Parameters (POST data, all optional)
* name (string)
* isBillable (tinyint)
* hourlyRate (decimal)
* budgetMinutes (int)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found
* 406 Duplicated: A project with the same name already exists

### Example
PUT `https://track.timeneye.com/api/3/projects/1245/`
Post Data: isBillable=0


## DELETE /projects/[ID]/

Deletes a project (PMs only).

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
DELETE `https://track.timeneye.com/api/3/projects/1245/`


## GET /projects/[ID]/tasks/

Returns a project's tasks. Some details are shown only to PMs and admins.

### Returns
* HTTP Code: 200 OK
* tasks
	* id (int)
	* name (string)
	* isOpen (tinyint)
	* categoryId (int)
	* categoryName (string)
	* budgetMinutes (int, PMs only)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted


### Example
GET `https://track.timeneye.com/api/3/projects/1323/tasks/`

API returns:

    {
    	"tasks":[
    		{
    			"id":"4461",
    			"name":"Control panel development",
    			"isOpen":1,
    			"categoryId":"-1",
    			"categoryName":"",
    			"budgetMinutes":"0"
    		},{
    			"id":"4457",
    			"name":"Gestionale Agenda Commerciale",
    			"isOpen":1,
    			"categoryId":"-1",
    			"categoryName":"",
    			"budgetMinutes":"0"
    		}
		]
	}
	

## POST /projects/[ID]/tasks/

Creates a new task

### Parameters (POST data)
* name (string)
* categoryId (int, optional)
* budgetHours (int, optional)

### Returns
* HTTP Code: 201 Created
* id (int)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted: you cannot create tasks
* 406 Duplicated

### Example
GET `https://track.timeneye.com/api/3/projects/1245/tasks/`
Post Data: name=My+Test+Task

API returns:

    {
        "id":5432
    }


## GET /projects/[ID]/tasks/[ID]

Returns task's details. Some details are shown only to PMs and admins.

### Returns
* HTTP Code: 200 OK
* id (int)
* name (string)
* isOpen (tinyint)
* categoryId (int)
* categoryName (string)
* budgetMinutes (int, PMs only)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
GET `https://track.timeneye.com/api/3/projects/1323/tasks/4534/`

API returns:

    {
        "id":"1014",
        "name":"Ciccio Pasticcio2",
        "isActive":"1",
        "clientId":"-1",
        "clientName":"",
        "isBillable":"0",
        "hourlyRate":"0.00",
        "budgetMinutes":"0"
	}


## PUT /projects/[ID]/tasks/[ID]/

Updates a task (PMs only).

### Parameters (POST data, all optional)
* name (string)
* categoryId (int)
* budgetHours (int)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
PUT `https://track.timeneye.com/api/3/projects/1245/tasks/5599/`
Post Data: name=New+name


## DELETE /projects/[ID]/tasks/[ID]/

Deletes a task (PMs only).

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
DELETE `https://track.timeneye.com/api/3/projects/1245/tasks/6692/`