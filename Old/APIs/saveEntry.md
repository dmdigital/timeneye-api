# saveEntry

Stores an entry, inserting or editing it (set entryId = -1 for inserts).

### Status

Stable.

### Params
* authToken (string)
* entryId (int): -1 for new insert
* entryDate (date)
* taskId (int)
* minutes (int)
* amount (float) [expenses]
* [notes (string)]

### Returns
* HTTP Code: 200 OK
* entryId (int)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Forbidden: you cannot access this task or entry
* 404 Not Found: time entry not found

### Example
Call `https://app.timeneye.com/api/2/saveEntry`, posting `authToken=yourauthtoken&entryId=-1&entryDate=2013-07-01&taskId=123456&minutes=120&amount=0.00`.

API returns:

    {
    	"entryId": "123456"
    }
	
