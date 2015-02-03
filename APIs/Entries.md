# Entries

### Status

Stable.


## GET /entries

Returns the list of entries.

### Parameters (POST data)
* dateFrom (string, optional, default 1 week ago)
* dateTo (string, optional)
* projectId (int, optional)
* taskId (int, optional)
* taskCategoryId (int, optional)
* userId (int, optional)
* limit (int, optional, default 20)
* offset (int, optional)

### Returns
* HTTP Code: 200 OK
* entries (array)
	* id (int)
	* entryDate (date)
	* projectId (int)
	* projectName (string)
	* userId (int)
	* userName (string)
	* taskId (int)
	* taskName (string)
	* notes (string)
	* minutes (int)
	* billed (tinyint)
	
### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
GET `https://track.timeneye.com/api/3/entries`

API returns:

    {
    	"entries":[
    		{
    			"id":"52402",
    			"entryDate":"2015-01-21",
    			"projectId":"872",
    			"projectName":"Indigo UX",
    			"userId":"110",
    			"userName":"Daniele Grassi",
    			"taskId":"4088",
    			"taskName":"Marketing",
    			"notes":"",
    			"minutes":"60",
    			"billed":"0"}
			}
		]
	}
	

## POST /entries

Registers a new time entry

### Parameters (POST data)
* projectId (int)
* taskId (int)
* minutes (int)
* userId (int, optional, default authenticated user)
* entryDate (date, optional, default today (GMT))
* notes (string, optional)

### Returns
* HTTP Code: 201 Created
* id (int)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
POST `https://track.timeneye.com/api/3/entries/`
Post Data: projectId=123&taskId=4542&minutes=45

API returns:

    {
        "id":1014
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