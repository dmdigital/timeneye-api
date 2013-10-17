# Timeneye API 2.0

## Overview

[Timeneye Time Tracking](http://www.timeneye.com "Timeneye Time Tracking") is a time tracking and reporting web app meant to be extremely simple and usable even for the most recalcitrant user.

Timeneye can be used from the web (<http://app.timeneye.com>) or from the [Android mobile app](https://play.google.com/store/apps/details?id=net.dmdigital.timeneye). An iOS version is currently in development.

Timeneye integrates with [Basecamp](http://www.basecamp.com), allowing users to [track time directly from Basecamp](http://www.timeneye.com/basecamp-time-tracking) commenting on their to-dos with the time spent on them.

## API System

You can integrate your apps with Timeneye, offering time tracking capabilities directly from there, using the public Timeneye API

### Status

The API is currently in development, with new endpoints being added over time. Currently, the 2.0 version of the API allows third-party apps to record time entries, retrieving projects, tasks, entries log, users.

### Authentication

Requests made to the API need to be authenticated providing an authToken in the post data. The authToken can be obtained using the authorizeUser() API call.

API calls are made through https.

### Data format

All the API requests are POSTs, and parameters need to be sent as classic POST parameters.

The API responses are characterized by a HTTP code (we use a set of about 10 possible response codes) and a JSON payload (when necessary)

Dates are in the MySQL format: YYYY-MM-DD HH:mm:ss

### Endpoint

All requests are made against endpoints like this: 
`https://app.timeneye.com/api/2/[apiName]`

Beta stage APIs are accessible only using the `https://beta.timeneye.com/api/2/[apiName]` endpoint.

### Available APIs

* [authorizeUser](./APIs/authorizeUser.md)
* [deauthorizeUser](./APIs/deauthorizeUser.md)
* [getEntries](./APIs/getEntries.md)
* [getEntry](./APIs/getEntry.md)
* [getProjects](./APIs/getProjects.md)
* [getProject](./APIs/getProject.md)
* [addUserToProject](./APIs/addUserToProject.md)
* [removeUserFromProject](./APIs/removeUserFromProject.md)
* [getUsers](./APIs/getUsers.md)
* [saveEntry](./APIs/saveEntry.md)
* [deleteEntry](./APIs/deleteEntry.md)
* [startTracking](./APIs/startTracking.md)

## Help us make it better

Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use GitHub issues. Fork these docs and send a pull request with improvements.
