# deauthorizeUser

Invalidates the authToken, logging the user off from every device which was connected using the API.

### Params
* authToken (string)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters

### Example
Call `https://app.timeneye.com/api/2/deauthorizeUser`, posting `authToken=yourauthtoken`.
