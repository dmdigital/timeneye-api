# getProjects

Returns a list of active projects.

### Params
* authToken (string)

### Returns
* HTTP Code: 200 OK
* projects (array)
	* projectId (int)
	* projectName (string)
	* weight (int)
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
	
