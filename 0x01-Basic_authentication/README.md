This contains files for Basic Auth task

### 1. **What Authentication Means**
Authentication is the process of verifying the identity of a user, system, or entity. It ensures that the person or system trying to access a resource is who they claim to be. Common methods of authentication include passwords, biometric data, two-factor authentication (2FA), and OAuth tokens.

### 2. **What Base64 Is**
Base64 is an encoding scheme used to convert binary data (such as images, files, or any other type of data) into ASCII text. It represents data in a 64-character alphabet (A-Z, a-z, 0-9, +, /). This encoding is often used in data transmission (e.g., email, HTTP headers) to ensure that binary data can be safely transferred over text-based protocols.

### 3. **How to Encode a String in Base64**
To encode a string in Base64, you can use various tools or programming languages. Here’s an example using Python:

```python
import base64
encoded_string = base64.b64encode("your_string_here".encode('utf-8')).decode('utf-8')
print(encoded_string)
```

Alternatively, you can use online tools or command-line utilities like `base64` in Linux:
```bash
echo -n "your_string_here" | base64
```

### 4. **What Basic Authentication Means**
Basic Authentication is a simple authentication scheme where the client sends the username and password encoded in Base64 in the HTTP `Authorization` header. The format is:
```
Authorization: Basic <Base64-encoded username:password>
```
It's considered less secure because it sends the credentials in every request (without encryption), so it’s recommended to use it over HTTPS.

### 5. **How to Send the Authorization Header**
To send the `Authorization` header in an HTTP request, the format is:
```
Authorization: Basic <Base64-encoded-username:password>
```

For example, using `curl`:
```bash
curl -H "Authorization: Basic dXNlcjpwYXNzd29yZA==" https://example.com/resource
```
Where `dXNlcjpwYXNzd29yZA==` is the Base64-encoded string of `user:password`.

In Python (using `requests` library):
```python
import requests
from requests.auth import HTTPBasicAuth

response = requests.get("https://example.com/resource", auth=HTTPBasicAuth('user', 'password'))
print(response.content)
```

### Summary:
- **Authentication** ensures identity verification.
- **Base64** encodes binary data into text.
- **Basic Authentication** uses Base64 encoding to send credentials in HTTP headers.
- Use the `Authorization` header to pass credentials in HTTP requests.

