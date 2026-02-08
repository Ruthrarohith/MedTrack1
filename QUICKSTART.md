# MedTrack - Quick Start Guide

## 🚀 Get Started in 5 Minutes

### 1️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 2️⃣ Configure AWS (Create .env file)
```env
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key
SNS_TOPIC_ARN=arn:aws:sns:us-east-1:615299730511:Medtrack
SECRET_KEY=supersecuritykey_medtrack_dev
```

### 3️⃣ Setup DynamoDB Tables
```bash
python aws_setup.py
```

### 4️⃣ Run the Application
```bash
python app.py
```

### 5️⃣ Access the App
Open browser: **http://localhost:5000**

---

## 🔑 Login

**Admin:**
- URL: http://localhost:5000/admin/login
- Email: `admin@example.com`
- Password: `password123`

**Patient:**
- Sign up at: http://localhost:5000/signup

---

## 📦 What's Included

| File | Purpose |
|------|---------|
| `app.py` | Main Flask application |
| `aws_setup.py` | DynamoDB table creation |
| `database_dynamo.py` | Database operations |
| `ml_engine.py` | AI/ML features |
| `sns_service.py` | Notifications |
| `static/` | CSS, JS, Images |
| `templates/` | HTML pages |

---

## ⚡ Common Commands

```bash
# Install dependencies
pip install -r requirements.txt

# Setup AWS tables
python aws_setup.py

# Run application
python app.py

# Run on specific port
# Edit app.py line 764: app.run(host="0.0.0.0", port=8080)
```

---

## 🐛 Quick Fixes

**Problem:** Module not found  
**Fix:** `pip install -r requirements.txt`

**Problem:** AWS credentials error  
**Fix:** Create `.env` file or run `aws configure`

**Problem:** Table not found  
**Fix:** Run `python aws_setup.py`

**Problem:** Port 5000 in use  
**Fix:** Change port in `app.py` line 764

---

## 📖 Full Documentation

See **README.md** for complete setup instructions and troubleshooting.
