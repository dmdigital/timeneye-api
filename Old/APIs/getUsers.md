# getUsers

Returns the list of users linked to the account. If showDisabled is set to "1", retrieves disabled users too.

### Status

Stable.

### Params
* authToken (string)
* [showDisabled (tinyint)]

### Returns
* HTTP Code: 200 OK
* users (array)
	* userId (int)
	* email (string)
	* name (string)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
Call `https://app.timeneye.com/api/2/getUsers`, posting `authToken=yourauthtoken`.

API returns:

    {
    	"users":[
    		{
    			"userId":"1",
    			"email":"grassi@dmdigital.it",
    			"name":"Daniele Grassi",
    			"enabled":"1"
    		},
    		{
    			"userId":"2",
    			"email":"anas@dmdigital.it",
    			"name":"Anas Bouhtouch",
    			"enabled":"0"
    		}
    	]
    }
	
