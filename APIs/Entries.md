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


## PUT /entries/[ID]/

Updates an entry.

### Parameters (POST data, all optional)
* projectId (int)
* taskId (int)
* minutes (int)
* userId (int, optional, default authenticated user)
* entryDate (date, optional, default today (GMT))
* notes (string, optional)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 404 Not found
* 406 Duplicated

### Example
PUT `https://track.timeneye.com/api/3/entries/1245/`
Post Data: notes=Conference+call


## DELETE /entries/[ID]/

Deletes an entry.

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
DELETE `https://track.timeneye.com/api/3/entries/1245/`