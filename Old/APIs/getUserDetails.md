# getUserDetails

Returns details for the current user and his/her account.

### Status

Beta.

### Params
* authToken (string)

### Returns
* HTTP Code: 200 OK
* userId: (int)
* userSettings (object)
	* countryCode (string)
* accountSettings (object)
	* currencySymbol (string)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid


### Example
Call `https://app.timeneye.com/api/2/getUserDetails`, posting `authToken=yourauthtoken`.

API returns:

    {
    	"userId":"1",
    	"userSettings":
    	    {
    			"countryCode":"IT"
    		},
    	"accountSettings":
    		{
    			"currencySymbol":"$"
    		}
    }
	
