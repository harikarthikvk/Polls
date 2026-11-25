# Django Polls — SUTT Backend Task 1.5

A polls web app built by following the official Django tutorial, ["Writing your first Django app"](https://docs.djangoproject.com/en/stable/intro/tutorial01/) (Parts 1–8).
Users can view poll questions, vote on a choice, and see the results. Admins can add and edit questions from the Django admin panel.
(readme was written by ai except teh answers to questions)

## Features

- List of the latest published polls
- Voting page for each question, with CSRF protection
- Results page showing the vote counts
- Customised Django admin (inline choices, filters, search)
- Automated tests for the models and views
- Static files (CSS and a background image)

## Tech stack

- Python 3.13
- Django
- SQLite (the default database)

## Project structure

```
djangotutorial/
├── manage.py
├── mysite/            # project settings and root URLs
└── polls/             # the polls app
    ├── models.py      # Question, Choice
    ├── views.py       # Index, Detail, Results, vote
    ├── urls.py
    ├── admin.py
    ├── tests.py
    ├── templates/
    └── static/
```

## Running it locally

```bash
git clone https://github.com/harikarthikvk/Polls.git
cd Polls
python -m venv venv
venv\Scripts\activate          # Windows
# source venv/bin/activate     # macOS / Linux
pip install django
cd djangotutorial
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Then open:
- Polls: http://127.0.0.1:8000/polls/
- Admin: http://127.0.0.1:8000/admin/

Run the tests:

```bash
python manage.py test polls
```

---

# How the Web Works

## 1. What actually happens, step by step, when you type a URL into your browser and hit Enter?
url is parsed into diff parts -> DNS lookup of domain to retrive the ip of the server -> 3 way connection with the server using tcp -> tls handshake for https -> http request -> server processes the requests and http response comes back -> browser renders the page


## 2. What are the client and the server, and how do they talk to each other?
client is something that asks for something and server is something that processes the request of client . client sends http request and server answers thru http response. tls encrypts it for https and these travel over tcp.


## 3. What is HTTP? What's inside a request and a response?
hypertext transfer protocol is a set of rules for the client and server to format the messages. it is stateless so the server doesnt remember anything

## 4. What's the difference between GET and POST, and when would you use each?
get method is used to read or fetch data. and the  data goes into the url as a query string. (for viewing pages or anywhere where nothign changes on th eserver)
post method is used to send data that changes something. and the data goes into the request body. (used for cases where data on server changes like submitting a form or creating a account)


## 5. What do status codes like 200, 302, 404 and 500 mean?
- **200**: Ok, Success
- **302**: Temporary redirect
- **404**: Resource not found at that location
- **500**: internal serveer error 


## 6. What jobs do HTML, CSS and JavaScript each do on a page?
- **HTML**: defines the strucutre and contents of the page
- **CSS**: it changes of the contents are presented, like colors, padding etc
- **JavaScript**: it is the code that runs in the browser and reacts to teh user. it can change page without reloading


## 7. How does a website remember who you are between pages? (Cookies and sessions)
websites use session tokens and cookies . session is stored on the server and is indentified by a random session id. cookie are small key value pair that hte server asks the browser to store using set-cookie header. after that the browser sends the cookie back on every request to the same site.
cookie store the session id and server uses that to identify u. 

## 8. In Django, how does a request travel through URLs, views, models and templates before a response comes back?
request -> server -> django -> middleware -> url routing -> view - > model - > template -> responser
(MTV model template view)

## 9. Why did the tutorial add `{% csrf_token %}` to the voting form?
this was added to prevent against cross site request forgery. which is when go to some site and that site can auto submit a from to that real site. ur browser would add attach ur sessio ncookie and hte site will assume it is u
csrf token rejects (403 forbidden) any request where the tokens dont mathc (it adds a hidden input with a secret key in hte cokie whch also lives on th edjango CsrfViewMiddleware)

---


## Resources used

- [Backend from First Principles]([https://www.youtube.com/](https://www.youtube.com/playlist?list=PLui3EUkuMTPgZcV0QhQrOcwMPcBCcd_Q1)) (videos 2–6)
- [MDN: Web standards](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Web_standards)
- [Django polls tutorial](https://docs.djangoproject.com/en/stable/intro/tutorial01/)
- [Django documentation](https://docs.djangoproject.com/)
