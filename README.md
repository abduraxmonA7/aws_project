University Timetable Application.
This is my Operating Systems final project.
It is a "University Timetable" web application developed using Flask, deployed on an AWS EC2 instance, and powered by a PostgreSQL database hosted on AWS RDS.
The application lets users select their academic level (Undergraduate or Graduate) and view the corresponding course timetable.

Folowing Features are implemented:
Developed using the Flask framework.
Integrated with PostgreSQL to manage course data.
Deployed on AWS (EC2 for hosting and RDS for database).

Technologies Used:
Python (Flask framework)
PostgreSQL
AWS EC2 (hosting)
AWS RDS (database)

Setup and Deployment Instructions:
1. Create an AWS account.

2. Set up an EC2 instance and configure the necessary security groups.
Create a PostgreSQL database RDS, ensuring it has public access.

3. Connect to the EC2 Instance
SSH into the EC2 instance using the following command:
ssh -i "C:\your_key_2_ec2.pem" ubuntu@<EC2_Public_IP>

4. Prepare the EC2 Instance by:
Updating the instance and installing the required dependencies:
sudo apt update
sudo apt install python3 python3-pip postgresql-client -y

5. Connect to the RDS PostgreSQL Database
Use the following command to connect to the RDS database:
psql -h <RDS_End_Point> -U <RDS_User> -d <RDS_Database_Name>

6. Set Up the Database Table
Create the timetable table by running these SQL commands:
CREATE TABLE timetable (
    id SERIAL PRIMARY KEY,
    course_name VARCHAR(100),
    level VARCHAR(20),
    day VARCHAR(20),
    time VARCHAR(20)
);

INSERT INTO timetable (course_name, level, day, time)
VALUES
    ('Computer Programming II', 'Undergraduate', 'Friday', '9:00 AM'),
    ('Operating Systems', 'Graduate', 'Friday', '11:30 AM'),
    ('Global Social Problems', 'Undergraduate', 'Thursday', '07:00 PM'),
    ('Calculus I', 'Graduate', 'Monday', '11:30 AM'),
    ('College Algebra', 'Undergraduate', 'Wednesday', '11:30 AM');
    
7. Set Up the Flask Application
Create a project folder:
mkdir my_project
cd my_project
touch app.py

Implement the Flask application in app.py to connect to the PostgreSQL database.

8. Design HTML Templates
Create a templates folder and add the index.html and timetable.html files with the required HTML content.
Add the static folder that contains the style.css file. This makes our application look nicer :)

9. Set Up a Virtual Environment
Create and activate a Python virtual environment:
python3 -m venv venv
source venv/bin/activate

10. Install Required Python Libraries
pip3 install pg8000
pip3 install --upgrade pip
pip3 install flask psycopg2-binary

11. Run the Flask Application
python app.py

12. Access the Application
Open a web browser and navigate to:
http://<EC2_Public_IP>:8000
