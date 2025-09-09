

## 🐳 Docker Setup

This project is containerized using Docker for consistent and reproducible deployment.

---

### 📁 Files Included

├── Dockerfile
├── requirements.txt
├── app.py

```

---

### ⚙️ Dockerfile

```Dockerfile
FROM python:3.8-slim
WORKDIR /app
COPY . /app
RUN pip install --no-cache-dir -r requirements.txt
EXPOSE 5000
ENV FLASK_APP=app.py
CMD ["flask", "run", "--host=0.0.0.0"]
```

---

### 🚀 Docker Workflow

#### 🔧 Build Image

```bash
docker build -t flask-app .
```

#### 📤 Tag & Push to Docker Hub

```bash
docker login
docker tag flask-app yourusername/flask-app:latest
docker push yourusername/flask-app:latest
```

#### 📥 Pull Image (on another machine)

```bash
docker pull yourusername/flask-app:latest
```

#### ▶️ Run Container

```bash
docker run -d -p 5000:5000 yourusername/flask-app:latest
```

#### 🔁 Restart or Re-run Container

```bash
docker ps                      # List running containers
docker stop <container_id>     # Stop container
docker rm <container_id>       # Remove container
docker run -d -p 5000:5000 yourusername/flask-app:latest  # Run again
```

---

### ✅ Notes

* Ensure `app.py` is at root level.
* Use `.dockerignore` to exclude unnecessary files.
* For development with live reload:

```bash
docker run -d -p 5000:5000 -v $PWD:/app flask-app
```

* For production, replace Flask dev server with Gunicorn:

```Dockerfile
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]
```



<pre><div><span><span>## 🐳 Docker Setup</span></span><span>

</span><span>This </span><span>project </span><span>is </span><span>containerized </span><span>using </span><span>Docker </span><span>for </span><span>consistent </span><span>and </span><span>reproducible </span><span>deployment.</span></div></pre>
