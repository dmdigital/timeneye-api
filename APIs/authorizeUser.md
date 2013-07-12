# authorizeUser

Exchanges email and password with an authToken.

### Params
* email (string)
* password (string)

### Returns
* HTTP Code: 200 OK
* authToken (string)

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: login failed

### Example
Call `https://app.timeneye.com/api/2/authorizeUser`, posting `email=your@email.com&password=yourpassword`.

API returns:
`{"authToken":"yourauthtoken"}`