# deleteEntry

Deletes an entry.

### Status

Stable.

### Params
* authToken (string)
* entryId (int)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: login failed
* 403 Forbidden: you cannot delete this entry
] 404 Not Found: time entry not found

### Example
Call `https://app.timeneye.com/api/2/deleteEntry`, posting `authToken=yourauthtoken&entryId=123456`.