# flask-app1
Sure! Below is a complete **Flask + Docker** project for a simple **User Registration Form** for an event — perfect to integrate in a **DevOps workflow** (Docker, GitHub, CI/CD, etc.).

---

## ✅ Project Structure

```
event-registration/
├── app.py
├── templates/
│   └── register.html
├── requirements.txt
└── Dockerfile
```

---

## 📝 `app.py` – Flask Backend

```python
from flask import Flask, render_template, request

app = Flask(__name__)

registrations = []

@app.route("/", methods=["GET", "POST"])
def register():
    if request.method == "POST":
        name = request.form["name"]
        email = request.form["email"]
        phone = request.form["phone"]

        registrations.append({
            "name": name,
            "email": email,
            "phone": phone
        })

        return f"Thank you {name}, you are registered!"

    return render_template("register.html")

if __name__ == "__main__":
    app.run(debug=True, host="0.0.0.0")
```

---

## 🖼️ `templates/register.html`

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Event Registration</title>
</head>
<body>
  <h2>Register for the Event</h2>
  <form method="post">
    Name: <input type="text" name="name" required><br><br>
    Email: <input type="email" name="email" required><br><br>
    Phone: <input type="text" name="phone" required><br><br>
    <button type="submit">Register</button>
  </form>
</body>
</html>
```

---

## 📦 `requirements.txt`

```
Flask
```

---

## 🐳 `Dockerfile`

```Dockerfile
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Copy files
COPY . .

# Install Flask
RUN pip install -r requirements.txt

# Expose port
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]
```

---

## 🚀 Docker Commands to Build and Run

### 🔨 Build Image

```bash
docker build -t event-registration .
```

### ▶️ Run Container

```bash
docker run -d -p 5000:5000 --name event-app event-registration
```

Open your browser: [http://localhost:5000](http://localhost:5000)

---

## ✅ DevOps Integration Ideas

You can now:

* 🧪 Add **unit tests**
* 📥 Push to **GitHub**
* ⚙️ Automate deployment with **GitHub Actions** or **Jenkins**
* 🚢 Use **Docker Compose** with a DB (e.g., MySQL/PostgreSQL)
* 🔧 Deploy to **Kubernetes**, **Heroku**, **Render**, etc.

---

Would you like help to:

* Add **form validation**?
* Save data to a **database**?
* Push to GitHub and deploy using **CI/CD**?

Let me know!
