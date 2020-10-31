# Twist

Twist is a lightweight WSGI web application framework. Its
designed to be simple and used in small applications but can
be scaled up to more complex applications if you so choose. 

Twist was made while following a tutrial by Jahongir Rahmonov. 
The link to his blog posts is here: https://rahmonov.me/posts/write-python-framework-part-one/

### Pip module coming soon!
I haven't had to time get the pip module setup but I will get it up and running very soon!

### Usage
If you want to use Twist without installing the pip module, 
you can just download this github repo and do it locally. 

Example App:
```python
from twist import Twist

app = Twist()


@app.route("/")
def home(req, resp):
    resp.text = "Hello, this is a home page."
```

If you want to deploy this app, I recommend you install
Gunicorn. Here is how you would deploy that code above
```text
gunicorn app:app
```
