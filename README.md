# MedTrack - Healthcare Management System

A comprehensive healthcare management system built with Flask and AWS services (DynamoDB, SNS, EC2).

## 📋 Table of Contents
- [Prerequisites](#prerequisites)
- [AWS Setup](#aws-setup)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [Features](#features)
- [Troubleshooting](#troubleshooting)

---

## 🔧 Prerequisites

Before running MedTrack, ensure you have the following installed:

1. **Python 3.8+**
   ```bash
   python --version
   ```

2. **AWS Account** with the following services enabled:
   - DynamoDB
   - SNS (Simple Notification Service)
   - EC2 (for deployment)
   - IAM (for access management)

3. **AWS CLI** configured with your credentials
   ```bash
   aws configure
   ```

---

## ☁️ AWS Setup

### Step 1: Configure AWS Credentials

Create a `.env` file in the project root with your AWS credentials:

```env
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=your_access_key_here
AWS_SECRET_ACCESS_KEY=your_secret_key_here
SNS_TOPIC_ARN=arn:aws:sns:us-east-1:YOUR_ACCOUNT_ID:Medtrack
SECRET_KEY=your_secret_key_for_flask
```

### Step 2: Create DynamoDB Tables

Run the AWS setup script to create all required DynamoDB tables:

```bash
python aws_setup.py
```

This will create the following tables:
- `medtrack_patients`
- `medtrack_doctors`
- `medtrack_appointments`
- `medtrack_medical_vault`
- `medtrack_blood_bank`
- `medtrack_invoices`
- `medtrack_chat_messages`
- `medtrack_mood_logs`

### Step 3: Configure SNS Topic

1. Go to AWS SNS Console
2. Create a topic named `Medtrack`
3. Subscribe your email for notifications
4. Update the `SNS_TOPIC_ARN` in your `.env` file

---

## 💻 Installation

### Step 1: Clone the Repository (if not already done)

```bash
cd c:\Users\rohit\Downloads\AWS-Captone\MedTrack
```

### Step 2: Create Virtual Environment (Recommended)

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate

# On Linux/Mac:
source venv/bin/activate
```

### Step 3: Install Dependencies

Choose one of the following based on your needs:

**Standard Installation:**
```bash
pip install -r requirements.txt
```

**Lite Installation (minimal dependencies):**
```bash
pip install -r requirements-lite.txt
```

---

## 🚀 Running the Application

### Local Development

1. **Ensure AWS credentials are configured** (see AWS Setup)

2. **Run the Flask application:**
   ```bash
   python app.py
   ```

3. **Access the application:**
   - Open your browser and navigate to: `http://localhost:5000`
   - Or: `http://127.0.0.1:5000`

### AWS EC2 Deployment

1. **Launch EC2 Instance** (Amazon Linux 2 or Ubuntu recommended)

2. **SSH into your instance:**
   ```bash
   ssh -i your-key.pem ec2-user@your-ec2-public-ip
   ```

3. **Install dependencies on EC2:**
   ```bash
   sudo yum update -y
   sudo yum install python3 python3-pip git -y
   ```

4. **Clone and setup the application:**
   ```bash
   git clone https://github.com/Ruthrarohith/MedTrack.git
   cd MedTrack
   pip3 install -r requirements.txt
   ```

5. **Configure environment variables:**
   ```bash
   nano .env
   # Add your AWS credentials and configuration
   ```

6. **Run the application:**
   ```bash
   python3 app.py
   ```

7. **Access via EC2 Public IP:**
   - `http://your-ec2-public-ip:5000`
   - Ensure Security Group allows inbound traffic on port 5000

---

## 📁 Project Structure

```
MedTrack/
├── app.py                    # Main Flask application
├── aws_setup.py              # AWS DynamoDB table setup script
├── database_dynamo.py        # DynamoDB database adapter
├── ml_engine.py              # Machine learning prediction engine
├── sns_service.py            # AWS SNS notification service
├── requirements.txt          # Python dependencies
├── requirements-lite.txt     # Minimal dependencies
├── .gitignore                # Git ignore rules
├── static/                   # Static assets (CSS, JS, images)
│   ├── css/
│   ├── js/
│   └── images/
└── templates/                # HTML templates
    ├── admin/                # Admin dashboard templates
    ├── doctor/               # Doctor dashboard templates
    ├── patient/              # Patient dashboard templates
    └── ai/                   # AI features templates
```

---

## ✨ Features

### For Patients:
- 📅 Book appointments with doctors
- 📊 View medical records in secure vault
- 💊 AI-powered symptom analysis
- 💬 Chat with healthcare providers
- 📧 Email/SMS notifications for appointments
- 💰 View and manage invoices
- 🩸 Blood donation requests

### For Doctors:
- 👥 Manage patient appointments
- 📋 View patient medical history
- 🤖 AI-assisted diagnosis tools
- 💬 Chat with patients
- 📊 Dashboard with analytics

### For Admins:
- 👨‍⚕️ Manage doctors and patients
- 📅 Oversee all appointments
- 🩸 Blood bank management
- 💰 Invoice and billing management
- 📊 Hospital capacity tracking

---

## 🔐 Default Login Credentials

### Admin Login:
- **URL:** `http://localhost:5000/admin/login`
- **Email:** `admin@example.com`
- **Password:** `password123`

### Creating New Users:
- Patients can sign up at: `http://localhost:5000/signup`
- Doctors and additional admins must be created via `aws_setup.py` script

---

## 🐛 Troubleshooting

### Issue: "ModuleNotFoundError"
**Solution:** Install missing dependencies
```bash
pip install -r requirements.txt
```

### Issue: "AWS credentials not found"
**Solution:** Configure AWS CLI or create `.env` file
```bash
aws configure
# OR
# Create .env file with AWS credentials
```

### Issue: "DynamoDB table not found"
**Solution:** Run the setup script
```bash
python aws_setup.py
```

### Issue: "Port 5000 already in use"
**Solution:** Kill the process or use a different port
```bash
# Find process using port 5000
netstat -ano | findstr :5000

# Kill the process (Windows)
taskkill /PID <process_id> /F

# Or modify app.py to use different port:
app.run(host="0.0.0.0", port=8080, debug=True)
```

### Issue: "SNS notifications not working"
**Solution:** 
1. Verify SNS topic ARN in `.env` file
2. Confirm email subscription in AWS SNS console
3. Check AWS IAM permissions for SNS

### Issue: "Request Timed Out" on EC2
**Solution:**
1. Check EC2 Security Group - allow inbound on port 5000
2. Verify application is running: `ps aux | grep python`
3. Check application logs for errors

---

## 📞 Support

For issues or questions:
- GitHub: [https://github.com/Ruthrarohith/MedTrack](https://github.com/Ruthrarohith/MedTrack)
- Email: Contact your system administrator

---

## 📄 License

This project is for educational and demonstration purposes.

---

## 🎯 Quick Start Checklist

- [ ] Python 3.8+ installed
- [ ] AWS account created
- [ ] AWS CLI configured
- [ ] `.env` file created with credentials
- [ ] Dependencies installed (`pip install -r requirements.txt`)
- [ ] DynamoDB tables created (`python aws_setup.py`)
- [ ] SNS topic configured and email subscribed
- [ ] Application running (`python app.py`)
- [ ] Accessed application at `http://localhost:5000`

---

**Last Updated:** February 2026
