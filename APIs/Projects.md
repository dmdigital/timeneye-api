# Projects

### Status

Stable.


## GET /projects

Returns the list of projects accessible by the user

### Returns
* HTTP Code: 200 OK
* projects (array)
	* id (int)
	* name (string)
	* isActive (tinyint)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
GET `https://track.timeneye.com/api/3/projects`

API returns:

    {
    	"projects":[
    		{
    			"id":"637",
    			"name":"Arduino UX",
    			"isActive":"1"
    		},
            {
                "id":"639",
                "name":"HyperLoop",
                "isActive":"1"
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
POST `https://track.timeneye.com/api/3/projects/`
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
GET `https://track.timeneye.com/api/3/projects/1014/`

API returns:

    {
        "id":"1014",
        "name":"My great project",
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


## GET /projects/[ID]/users/

Returns a project's users. If requesting user is not PM, returns only himself.

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
GET `https://track.timeneye.com/api/3/projects/1323/users/`

API returns:

    {
    	"users":[
    		{
    			"id":"127",
    			"name":"d.grassi84@gmail.com",
    			"isPM":1
    		}
    	]
    }
	

## POST /projects/[ID]/users/

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


## PUT /projects/[ID]/users/[ID]/

Updates a user (PMs only).

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
PUT `https://track.timeneye.com/api/3/projects/1245/users/5599/`
Post Data: budgetHours=23


## DELETE /projects/[ID]/users/[ID]/

Removes a user from a project.

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
DELETE `https://track.timeneye.com/api/3/projects/1245/users/6692/`