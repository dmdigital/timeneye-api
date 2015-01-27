# removeUserFromProject

Revokes project access permissions to the specified user (targetId). Works only for limited access projects

### Status

Beta.

### Access

Account Owners or Project Managers with access to the specified project.

### Params
* authToken (string)
* projectId (int)
* targetId (int)

### Returns
* HTTP Code: 200 OK

### Errors
* 400 Bad Request: missing required parameters
* 401 Unauthorized: authToken not valid
* 403 Forbidden: access denied
* 405 Method not allowed: specified project is not private

### Example
Call `https://app.timeneye.com/api/2/removeUserFromProject`, posting `authToken=yourauthtoken&projectId=123&targetId=43534`.	
