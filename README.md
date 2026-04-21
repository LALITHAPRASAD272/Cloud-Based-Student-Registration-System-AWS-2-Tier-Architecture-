 Cloud-Based Student Registration System (AWS 2-Tier Architecture)
 Overview

This project demonstrates the deployment of a scalable web-based Student Registration System using a 2-tier architecture on AWS.

Application Layer runs on AWS EC2
Database Layer runs on AWS RDS (MySQL)

The system allows users to perform CRUD operations on student data through a web interface.

 Objective
Design and deploy a cloud-based web application
Implement a 2-tier architecture (Application + Database)
Enable CRUD operations for student records
Ensure secure communication between application and database
 Architecture
User → EC2 (Flask App) → RDS (MySQL Database)
Layers:
Application Layer
Handles user requests
Hosted on EC2
Database Layer
Stores student records
Managed by RDS (MySQL)
 Technologies Used
Python (Flask)
AWS EC2
AWS RDS (MySQL)
REST API
Gunicorn (Production Server)
 AWS Resources
1. Network Environment
Secure cloud network setup
Controlled communication between services
2. Application Server (EC2)
Hosts Flask application
Handles API requests
3. Database Server (RDS)
Managed MySQL database
Stores student data securely
 Security Configuration
EC2 Security Group
SSH (Port 22) → Admin access (restricted IP)
HTTP (Port 80) → Public access
Custom Port (5000) → Flask app access
RDS Security Group
MySQL (Port 3306) → Accessible only from EC2
Best Practices
Database not publicly accessible
Restricted SSH access
Principle of least privilege
Secure internal communication
 Setup & Installation
1. System Setup
sudo dnf update -y
sudo dnf install python3-pip -y
python3 --version
pip3 --version
2. Install Dependencies
pip3 install flask
pip3 install flask-sqlalchemy
pip3 install pymysql
pip3 install gunicorn
3. Project Setup
mkdir student-app
cd student-app
mkdir templates
 Environment Variables
export DB_HOST='your-rds-endpoint'
export DB_USER='admin'
export DB_PASSWORD='your-password'
export DB_NAME='studentdb'
 Run Application
Development Mode
python3 app.py
Production Mode
gunicorn -w 2 -b 0.0.0.0:5000 app:app --daemon
 Access Application

Open browser:

http://<EC2-PUBLIC-IP>:5000

Test API:

curl http://localhost:5000
 Features
 Add student records
 View all students
 View student by ID
 Delete student records
 API Endpoints
Method	Endpoint	Description
GET	/students	Get all students
GET	/student/	Get student by ID
POST	/student	Add student
DELETE	/student/	Delete student
 Project Structure
student-app/
│── app.py
│── templates/
│── models/
│── config/
 Challenges
Secure communication between EC2 and RDS
Cloud networking configuration
Debugging connectivity issues
 Solutions
Proper security group configuration
Restricted database access
Verified network permissions
 Outcome
Successfully deployed a cloud-based application
Implemented secure 2-tier architecture
Application accessible via public endpoint
 Conclusion

This project demonstrates real-world cloud deployment using AWS and a structured 2-tier architecture. It provides a strong foundation for:

Scalable systems
Microservices architecture
DevOps practices
