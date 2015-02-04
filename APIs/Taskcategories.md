# Task Categories

### Status

Stable.


## GET /taskcategories

Returns the list of account task categories (admin only)

### Returns
* HTTP Code: 200 OK
* categories (array)
	* id (int)
	* name (string)
	
### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
GET `https://track.timeneye.com/api/3/taskcategories/`

API returns:

    {
    	"categories":[
    		{
    			"id":"127",
    			"name":"Web Development"
    		}
		]
	}