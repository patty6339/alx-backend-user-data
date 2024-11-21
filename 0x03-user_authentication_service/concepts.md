### 1. **How to declare API routes in a Flask app:**
   - In Flask, API routes are declared using the `@app.route()` decorator. The route specifies the URL pattern and the HTTP methods (GET, POST, etc.) that the endpoint should respond to.
   ```python
   from flask import Flask

   app = Flask(__name__)

   @app.route('/api/hello', methods=['GET'])
   def hello():
       return 'Hello, World!'

   if __name__ == '__main__':
       app.run()
   ```
   - The `@app.route()` decorator binds the function to the route and HTTP method.

---

### 2. **How to get and set cookies:**
   - **Get a cookie**: Use `request.cookies.get()` to retrieve a cookie.
   - **Set a cookie**: Use `response.set_cookie()` to send a cookie in the response.
   ```python
   from flask import Flask, request, make_response

   app = Flask(__name__)

   @app.route('/set_cookie')
   def set_cookie():
       resp = make_response('Cookie Set!')
       resp.set_cookie('username', 'john_doe')
       return resp

   @app.route('/get_cookie')
   def get_cookie():
       username = request.cookies.get('username')
       return f'Hello, {username}!'
   ```

---

### 3. **How to retrieve request form data:**
   - You can use `request.form` to retrieve form data sent with a POST request.
   ```python
   from flask import Flask, request

   app = Flask(__name__)

   @app.route('/submit', methods=['POST'])
   def submit():
       username = request.form.get('username')
       password = request.form.get('password')
       return f'Username: {username}, Password: {password}'
   ```

---

### 4. **How to return various HTTP status codes:**
   - You can return HTTP status codes by passing them as the second argument in the `return` statement.
   ```python
   from flask import Flask, jsonify

   app = Flask(__name__)

   @app.route('/success')
   def success():
       return 'Success', 200  # HTTP 200 OK

   @app.route('/created')
   def created():
       return 'Resource Created', 201  # HTTP 201 Created

   @app.route('/not_found')
   def not_found():
       return 'Not Found', 404  # HTTP 404 Not Found

   @app.route('/error')
   def error():
       return jsonify({'error': 'Internal Server Error'}), 500  # HTTP 500 Internal Server Error
   ```

These are the basic methods for handling routes, cookies, form data, and status codes in a Flask application.
