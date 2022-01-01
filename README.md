![The Logo](twistLogo.png)

Twist is a lightweight WSGI web application framework. Its
designed to be simple and used in small applications but can
be scaled up to more complex applications if you so choose. 

Twist wouldn't be possible without the amazing blog posts and tutorials from Jahongir Rahmonov. 
Make sure to go follow his Github Profile here: https://github.com/rahmonov and star a couple of his projects. 
I'm sure that would make his day just a little better. The link to his blog post is here: 
https://rahmonov.me/posts/write-python-framework-part-one/

## The Beginning
To be able to use Twist at the moment, you have to download all the files
locally and play with it from there since there is no pip module for it yet
(coming very soon!). Many apologies for this inconvenience!

Example "Hello World" App in Twist:
```python
# app.py
from twist import Twist

app = Twist()

@app.route("/")
def home(req, resp):
    resp.text = "Hello World! This is Twist!"
```

If you want to deploy this app, I recommend you install
Gunicorn (Please keep in mind that Gunicorn is Unix only. You may need to use another WSGI service). Here is how you would deploy that code above:
```text
gunicorn app:app
```
Side note: Please install the dependencies! This project will not work as its supposed to without them. If you don't know how to install these, use `pip3 install -r requirements.txt`.

## How does Twist handle handlers?
Twist uses classed based handlers which can be easily implemented in just a few lines of code. Here's
an example:
```python
@app.route("/")
def home(req, resp):
    resp.text = "Hello, How are you?"
```
The example handler above only takes in `GET` requests. No `POST` requests here! Function-based handlers
can also do the same thing. Take a look at the example below:
```python
@app.route("/", methods=["get"])
def home(req, resp):
    resp.text = "Hello, How are you?"
```

## How does Twist deal with templates?
Templates are currently supported in Twist. To find these templates, find the `templates` folder. You can add it to the init class at the beginning of your app like so:
```python
app = Twist(templates_dir="test.html")
```
Then, you can use the HTML files in a handler. Like so:
```python
@app.route("/show/template")
def handler_with_template(req, resp):
    resp.html = app.template("test.html", context={"title": "Twist Framework is so cool!", "body": "Twist - A Python Framework"})
```

## WIP
Please keep in mind that this is a work-in-progress and I have no intention of abandoning the project in the future. Feel free to suggest any changes!
