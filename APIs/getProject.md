# getProject

Returns a project's details. fixedAmount and hourlyRate are returned only if user has permissions to see them.

### Params
* authToken (string)
* projectId (int)

### Returns
* HTTP Code: 200 OK
* project (array)
	* projectId (int)
	* projectName (string)
	* fixedAmount (decimal)
	* hourlyRate (decimal)
	* active (tinyint)
	* tasks (array)
		* taskId (int)
		* taskName (string)
		* isOpen (tinyInt)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Not Permitted: you cannot access to the requested project

### Example
Call `https://app.timeneye.com/api/2/getProject`, posting `authToken=yourauthtoken&projectId=123`.

API returns:

    {
    	"project":{
    		"projectId":"637",
    		"projectName":"Arduino UX",
    		"active":"1",
    		"fixedAmount":"1450.00",
    		"hourlyRate":"45.00",
    		"tasks":[
    			{
    				"taskId":"2247",
    				"taskName":"Marketing",
    				"isOpen":"1"
    			},
    			{
    				"taskId":"2248",
    				"taskName":"Pre-design",
    				"isOpen":"0"
    			}
    		]
    	}
    }
	
