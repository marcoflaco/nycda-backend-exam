## NYCDA Backend Exam
=====================
Explain the questions well!!

### 1- Why do we should include script tags at the very end of an html file, before closing </body>?
If you put it at the begin, it will read first the tags. putting at the end read first the code. wich is better eand faster.
putting at the begin cause a bad user experience. Your website basically stops loading until you've downloaded all scripts. If there's one thing that users hate it's waiting for a website to load.
### 2 - What is a middleware?
Middleware is any number of functions that are invoked by the Express.js
Middleware functions can perform the following tasks:

Execute any code.
Make changes to the request and the response objects.
End the request-response cycle.
Call the next middleware function in the stack.

### 3 - Why do we use express.static() middleware?
To serve static files such as images, CSS files, and JavaScript files, use the express.static built-in middleware function in Express.
we use that to read the public folder where for example you can storage images.

### 4 - What is favicon.ico ?
It's the little icon beside your site's name in the favorites list, before the URL in the address bar and bookmarks folder

### 5 - Why do we use a bodyParser middleware ?
 Body-parser extracts the entire body portion of an incoming request stream and exposes it on req.body

### 6 - What is the difference in terms of parsing a data received from a web form with POST or an AJAX POST request?
dont know


### 7 - Why do we use methodOverride middleware ?
use HTTP verbs such as PUT or DELETE in places where the client doesn't support it.
If you want to simulate DELETE and PUT, methodOverride is for that

### 8 - What are the differences between sessions and cookies ?
 Sessions have a unique identifier that maps them to specific users. This identifier can be passed in the URL or saved into a session cookie.
Sessions are server-side files that contain user information, while cookies are client-side files

### 9 - Why do we use a session middleware ?
A session store is a provision for storing session data in the backend. Sessions based on session stores can store a large amount of data that is well hidden from the user.

### 10 - Why do we use a build process ?
you can use gulp for example to allow for task automation. Also take all your projects html,js,css, concatenate them and minify them
