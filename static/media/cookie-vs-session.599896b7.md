Cookie:

A cookie is a key-value pair that is stored in the browser, and is sent to the server with each http request.

Session:

A session is an object that is stored in the server for a period of time. Session is implemented based on cookie. Typically a session id is stored in a cookie, and is sent to the server from the browser.

Local Storage Vs. Cookie

1. size limit, cookie generally has 4kb limitation whereas local storage has 5mb.
2. Cookie usually stores user info, such as user preferences, local storage stores less important data about user.
3. Cookie is sent to the server, local storage stays in the browser.

Local storage Vs. Session storage

1. local storage will not expire, session storage will expire when a session ends.
