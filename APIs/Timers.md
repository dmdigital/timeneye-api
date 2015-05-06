# Timers

### Status

Beta.


## GET /timers

Returns a list of user's timers.

### Returns
* HTTP Code: 200 OK
* timers (array)
	* id (int)
	* projectId (int)
	* projectName (string)
	* taskId (int)
	* taskName (string)
	* notes (string)
	* timerStatus (string, "running" or "paused")
	* currentSeconds (int, timer's seconds as for now)
	* updatedDatetime (datetime)
	* timerDate (date)
	
### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
GET `https://track.timeneye.com/api/3/timers`

API returns:

    {
    "timers": [
        {
            "id": "12",
            "projectId": "1589",
            "projectName": "CoolStartup Web Portal",
            "taskId": "5486",
            "taskName": "Research",
            "timerStart": "2015-03-30 09:10:18",
            "timerStatus": "running",
            "seconds": "121",
            "notes": "",
            "updatedDatetime": "2015-03-30 10:10:18"
        },
        {
            "id": "11",
            "projectId": "1589",
            "projectName": "CoolStartup Web Portal",
            "taskId": "5484",
            "taskName": "Design & Graphics",
            "timerStart": "2015-03-30 09:10:13",
            "timerStatus": "paused",
            "seconds": "113",
            "notes": "",
            "updatedDatetime": "2015-03-30 10:10:13"
        }
    ]}
	

## POST /timers

Starts a new timer

### Parameters (POST data)
* projectId (int)
* taskId (int)
* seconds (int)
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
POST `https://track.timeneye.com/api/3/timers/`
Post Data: projectId=123&taskId=4542

API returns:

    {
        "id":1014
    }


## PUT /timers/[ID]/

Updates a timer.

### Parameters (GET data, all optional)
* projectId (int)
* taskId (int)
* seconds (int)
* notes (string)
* timerDate (date)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 404 Not found
* 406 Duplicated

### Example
PUT `https://track.timeneye.com/api/3/timers/1245/`
Get Data: notes=Conference+call


## DELETE /timers/[ID]/

Deletes a timer.

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
DELETE `https://track.timeneye.com/api/3/timers/1245/`


## POST /timer/ID/

Stops a timer and stores it as a entry

### Parameters (POST data)
* timerId (int)

### Returns
* HTTP Code: 201 Created
* id (int, entry ID)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not permitted
* 404 Not found

### Example
POST `https://track.timeneye.com/api/3/timers/12/`

API returns:

    {
        "id":1014
    }