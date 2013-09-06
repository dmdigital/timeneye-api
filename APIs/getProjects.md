# getProjects

Returns a list of projects. By default, it returns active projects only. fixedAmount and hourlyRate are returned only if user has permissions to see them.

### Params
* authToken (string)
* [showInactive (tinyint), default = 0]

### Returns
* HTTP Code: 200 OK
* projects (array)
	* projectId (int)
	* projectName (string)
	* fixedAmount (decimal)
	* hourlyRate (decimal)
	* weight (int)
	* active (tinyint)
	* tasks (array)
		* taskId (int)
		* taskName (string)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
Call `https://app.timeneye.com/api/2/getProjects`, posting `authToken=yourauthtoken`.

API returns:

    {
    	"projects":[
    		{
    			"projectId":"637",
    			"projectName":"Arduino UX",
    			"weight":"2",
    			"active":"1",
    			"tasks":[
    				{
    					"taskId":"2247",
    					"taskName":"Marketing"
    				},
    				{
    					"taskId":"2248",
    					"taskName":"Pre-design"
    				}
    			]
    		}
    	]
    }
	
