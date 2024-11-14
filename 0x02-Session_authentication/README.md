Here's a summary of each term:

### 1. **What Authentication Means**
   - **Authentication** is the process of verifying a user's identity. It usually requires the user to provide credentials (like a username and password) to prove they are who they claim to be. This step ensures that only authorized users can access certain resources or perform certain actions within an application.

### 2. **What Session Authentication Means**
   - **Session Authentication** involves creating a session on the server for a user once they successfully log in. The server then assigns a unique session ID to the user, typically stored in a cookie. This session ID is sent with each subsequent request, allowing the server to authenticate the user throughout their interaction with the application without re-entering credentials.

### 3. **What Cookies Are**
   - **Cookies** are small pieces of data stored on the client’s browser by the server. They are used to retain information across multiple requests, such as session identifiers, preferences, or tracking data. Cookies help in maintaining user state and are often used in session-based authentication.

### 4. **How to Send Cookies**
   - Cookies can be sent from the server to the client by including a `Set-Cookie` header in the HTTP response. For example:
     ```http
     Set-Cookie: sessionId=abc123; HttpOnly; Secure; Path=/
     ```
   - This header tells the browser to store the cookie, and the browser will automatically send it with subsequent requests to the same server.

### 5. **How to Parse Cookies**
   - Cookies sent by the client are included in the `Cookie` header of the HTTP request. To parse cookies, you can read this header and split the cookies by `;` to retrieve each key-value pair. In JavaScript (Node.js), you might use the `cookie-parser` middleware or split the string manually:
     ```javascript
     const cookies = req.headers.cookie.split(';').reduce((acc, cookie) => {
       const [key, value] = cookie.trim().split('=');
       acc[key] = value;
       return acc;
     }, {});
     ```
