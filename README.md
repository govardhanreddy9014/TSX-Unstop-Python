# TSX-Unstop-Python
portfolio/
│
├── static/
│   └── style.css
├── templates/
│   ├── base.html
│   ├── index.html
│   ├── about.html
│   ├── projects.html
│   └── contact.html
├── app.py
└── requirements.txt


from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html')

@app.route('/about')
def about():
    return render_template('about.html')

@app.route('/projects')
def projects():
    return render_template('projects.html')

@app.route('/contact', methods=['GET', 'POST'])
def contact():
    if request.method == 'POST':
        name = request.form.get('name')
        email = request.form.get('email')
        message = request.form.get('message')
        # Here you would normally handle/store the form data
        return render_template('contact.html', success=True)
    return render_template('contact.html')

if __name__ == '__main__':
    app.run(debug=True)




    <!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>{% block title %}My Portfolio{% endblock %}</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
  <header>
    <nav>
      <a href="/">Home</a>
      <a href="/about">About</a>
      <a href="/projects">Projects</a>
      <a href="/contact">Contact</a>
    </nav>
  </header>

  <main>
    {% block content %}{% endblock %}
  </main>

  <footer>
    <p>&copy; 2025 My Portfolio</p>
  </footer>
</body>
</html>



{% extends 'base.html' %}
{% block title %}Home{% endblock %}
{% block content %}
<h1>Welcome to My Portfolio</h1>
<p>This is the homepage of my professional portfolio.</p>
{% endblock %}



{% extends 'base.html' %}
{% block title %}Contact{% endblock %}
{% block content %}
<h1>Contact Me</h1>
{% if success %}
  <p>Thank you for your message!</p>
{% else %}
<form method="POST">
  <label>Name:</label><br>
  <input type="text" name="name" required><br>
  <label>Email:</label><br>
  <input type="email" name="email" required><br>
  <label>Message:</label><br>
  <textarea name="message" required></textarea><br>
  <button type="submit">Send</button>
</form>
{% endif %}
{% endblock %}




body {
  font-family: Arial, sans-serif;
  padding: 20px;
  margin: 0;
}

nav a {
  margin: 0 15px;
  text-decoration: none;
}

footer {
  margin-top: 40px;
  text-align: center;
  color: #777;
}



Flask==2.3.2

pip install -r requirements.txt
