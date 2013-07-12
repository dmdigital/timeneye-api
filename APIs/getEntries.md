# getEntries

Returns a list of entries. You can filter it by projectId, dateFrom, dateTo or userId (the latter is only available for project managers or account owners); you can use offset and limit to paginate the results.

### Params
* authToken (string)
* [projectId (int)]
* [dateFrom (date)]
* [dateTo (date)]
* [userId (int)]
* [offset (int)]
* [limit (int)]

### Returns
* HTTP Code: 200 OK
* entries (array)
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
* 403 Forbidden: insufficient permissions

### Example
Call `https://app.timeneye.com/api/2/getEntries`, posting `authToken=yourauthtoken`.

API returns:

    {
    	"entries":[
			{
				"entryId":"6427",
				"entryDate":"2013-07-11",
				"projectId":"87",
				"projectName":"Gestione interna",
				"taskId":"1219",
				"taskName":"Commerciale",
				"minutes":"60",
				"amount":"0.00",
				"notes":"Meeting with Don",
				"billed":"0"
			},
			{
				"entryId":"6409",
				"entryDate":"2013-07-11",
				"projectId":"6",
				"projectName":"Timeneye",
				"taskId":"3576",
				"taskName":"[Timeneye 2.4] Sviluppo web",
				"minutes":"15",
				"amount":"0.00",
				"notes":"Worked on Status Page",
				"billed":
				"0"
			}
		]
	}
	
