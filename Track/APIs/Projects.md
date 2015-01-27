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
* projectId (int)

### Errors
* 400 Bad Request: missing required parameters | Name is too short
* 401 Unauthorized: authToken not valid
* 403 Not permitted: you cannot create projects
* 406 Duplicated

### Example
POST `https://track.timeneye.com/api/3/projects`
Post Data: name=My+Test+Project

API returns:

    {
        "projectId":1014
    }