# Timeneye API 10.0 - track.timeneye.com

*** This API refers to https://track.timeneye.com. ***

## Overview

[Timeneye Time Tracking](http://www.timeneye.com "Timeneye Time Tracking") is a time tracking and reporting web app meant to be extremely simple and usable even for the most recalcitrant user.

Timeneye can be used from the web (<http://track.timeneye.com>), from the [Android mobile app](https://play.google.com/store/apps/details?id=net.dmdigital.timeneye) and from the [iOS mobile app](https://itunes.apple.com/gb/app/timeneye/id940123759?mt=8).

Timeneye integrates with [Basecamp](http://www.basecamp.com), allowing users to [track time directly from Basecamp](https://www.timeneye.com/features/basecamp-time-tracking-integration) commenting on their to-dos with the time spent on them.

## API System

You can integrate your apps with Timeneye, offering time tracking capabilities directly from there, using the public Timeneye API

### Status

The API is currently in development, with new endpoints being added over time. Currently, the 10.0 version of the API allows third-party apps to manage projects, users and entries.

### Authentication

The API supports an OAuth 2.0 flow. External applications needs to register at https://track.timeneye.com/developers to obtain their `clientId` and `clientSecret`, and set their `redirectUri` where users should be redirected upon authentication.

- External applications redirect the user to a specific page on Timeneye: `https://track.timeneye.com/authorize/[clientId]`
- User authorizes the application to access its Timeneye data
- User is redirected to the application's `redirectUri` with an additional `code` parameter
- The application exchanges the `code` parameter with an accessToken using the `https://track.timeneye.com/token` endpoint. This request has to be made specifying a specific header: `Authorization: Basic XXX`, where `XXX` is `base64('[clientId]:[clientSecret]')`.
- A JSON structure is returned, containing `accessToken`, `refreshToken` and `expiration`.
- Subsequent calls can be made using the `accessToken` set in a specific header: `Bearer: [accessToken]`.

API calls are made throught https.

### Data format

The API responses are characterized by a HTTP code (we use a set of about 10 possible response codes) and a JSON payload (when necessary)

Dates are in the MySQL format, GMT: YYYY-MM-DD HH:mm:ss

### Available sections

* [Projects](./APIs/Projects.md)

## Help us make it better

Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use GitHub issues. Fork these docs and send a pull request with improvements.
