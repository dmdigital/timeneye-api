# getUsers

Returns the list of users linked to the account.

### Status

Stable.

### Params
* authToken (string)

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
    			"name":"Daniele Grassi"
    		},
    		{
    			"userId":"2",
    			"email":"anas@dmdigital.it",
    			"name":"Anas Bouhtouch"
    		}
    	]
    }
	
