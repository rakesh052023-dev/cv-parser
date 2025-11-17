# cv-parser (Resume Parser API)

This is a simple **resume parsing API** built with **Flask** and packaged in **Docker**,
ready to deploy to **Render**.

## Endpoints

- `GET /` — Health check, returns a simple message.
- `POST /extract` — Accepts a PDF resume and returns JSON with:
  - name
  - email
  - phone
  - skills
  - education
  - experience

### Example (Postman)

- Method: POST  
- URL: `https://YOUR-RENDER-URL.onrender.com/extract`  
- Body: `form-data`  
  - Key: `file` (type: File)
  - Value: your_resume.pdf

## Local development

```bash
pip install -r requirements.txt
python app.py
# Visit http://localhost:5000
```

## Docker (local)

```bash
docker build -t cv-parser .
docker run -p 5000:5000 -e PORT=5000 cv-parser
# Visit http://localhost:5000
```

## Deploy to Render

1. Push this project to a GitHub repo.
2. Create a new *Web Service* on Render.
3. Choose **Environment = Docker**.
4. Set **Root Directory** to `./`.
5. Set **Dockerfile path** to `Dockerfile`.
6. Render will automatically set `PORT`.
7. Deploy and use `/extract` endpoint.
