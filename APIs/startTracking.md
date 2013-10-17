# startTracking

Notifies Timeneye that the user has started working on a particular project (this information is reflected on the Status page).

### Status

Stable.

### Params
* authToken (string)
* projectid (nt)
* [taskId (int)]

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Forbidden: not authorized
* 404 Not Found: project or task not found

### Example
Call `https://app.timeneye.com/api/2/startTracking`, posting `authToken=yourauthtoken&projectId=12345`.