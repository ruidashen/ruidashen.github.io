# HTTP Methods - GET Vs. POST

## Differences between a GET request and a POST request:

- The GET request is harmless when the browser goes back to the last page, while the POST request is resubmitted.
- URL created by POST cannot be bookmarked.
- Browser will cache GET request automatically, however POST request won't unless set up manually.
- GET requests can only be URL encoded, POST supports multiple encoding methods
- GET request parameters are kept intact in the browser history, whereas POST parameters are not.
- GET requests have a limit on the length of parameters passed in the URL, while POST does not.
- GET only accepts ASCII characters for parameter, while POST has no restrictions.
- GET is more insecure than POST because the parameters are exposed directly to the URL, so it cannot be used to pass sensitive information.
- GET parameters are passed through the URL, while POST is placed in the Request body.

## Another major difference:

- GET produces one TCP packet; POST produces two TCP packets.

For GET requests, the browser sends the http header and data together, and the server responds with 200 (returned data).

For POST, the browser sends the header first, the server responds 100 continue, the browser sends the data again, the server responds 200 ok (return data), however this is browser specific.
