# getEntry

Returns details for the requested entry. Only user's entries can be retrieved.

### Status

Stable.

### Params
* authToken (string)
* entryId (int)

### Returns
* HTTP Code: 200 OK
* entry (object)
	* entryId (int)
	* entryDate (date)
	* projectId (int)
	* projectName (string)
	* taskId (int)
	* taskName (string)
	* minutes (int)
	* amount (float)
	* notes (text)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Forbidden: you cannot read this entry
* 404 Not Found: time entry not found


### Example
Call `https://app.timeneye.com/api/2/getEntry`, posting `authToken=yourauthtoken&entryId=123456`.

API returns:

    {
    	"entry":{
			"entryId":"100",
			"entryDate":"2013-02-15",
			"projectId":"44",
			"projectName":"Ovile - Gestionale",
			"taskId":"62",
			"taskName":"Progettazione",
			"minutes":"240",
			"amount":"0.00",
			"notes":"SRS e Progettazione",
			"billed":"0"
		}
	}
	
