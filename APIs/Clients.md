# Clients

### Status

Stable.


## GET /clients

Returns the list of account clients (admin only)

### Returns
* HTTP Code: 200 OK
* clients (array)
	* id (int)
	* name (string)
	
### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid

### Example
GET `https://track.timeneye.com/api/3/clients/`

API returns:

    {
    	"clients":[
    		{
    			"id":"127",
    			"name":"AB Consulting Group"
    		}
		]
	}