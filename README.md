# SOEN-6471-iCare-Group-F
Advanced Software Architecture - iCare System Project

Db.txt

#First create a Mysql DB user with uname= root & password= root
#copy paste the below DB queries (might chnage, just an init commit)


CREATE USER 'iCareRoot'@'localhost' IDENTIFIED BY 'root';
GRANT ALL PRIVILEGES ON iCare.* TO 'iCareRoot'@'localhost';

If you already have a DB user created.
---------------------------------------------------
Chnage the User name and the password in ---------
---------------------------------------------------
AdminDAO.java
DoctorDAO.java
WelcomeAdmin.jsp
Welcome.jsp
PatientDao.jsp
---------------------------------------------------


-Make sure you create the Db with the following SQl Queries only.

CREATE DATABASE iCare;
USE iCare;

CREATE TABLE patients(
   Pid int NOT NULL AUTO_INCREMENT,
   NAME VARCHAR (20)     NOT NULL,
   password VARCHAR(20)  NOT NULL,
   email VARCHAR(50),
   gender VARCHAR(50),
   PRIMARY KEY (Pid)    
);

CREATE TABLE doctors(
   did int NOT NULL AUTO_INCREMENT,
   NAME VARCHAR (20), 
   PRIMARY KEY (did)    
);


Create table doctor_login(
username varchar(20) NOT NULL,
password varchar(45) NOT NULL,
name varchar(20) NOT NULL,
department varchar(45) NOT NULL,
Primary key (username)
);

CREATE TABLE booking(
   bid int NOT NULL AUTO_INCREMENT,
   dtime DATETIME  NOT NULL,  
   PRIMARY KEY (bid),
   Pid integer,
   username VARCHAR(20),
   FOREIGN KEY (Pid) REFERENCES patients(Pid),
   FOREIGN KEY (username) REFERENCES doctor_login(username)  
);


INSERT INTO doctor_login(name, username, password, department)
VALUES	('Alice Doe', 'alice', 'psswd123', 'none'),
		('Bob Doe', 'bob', 'psswd123', 'none'),
		('Carl Johnson', 'cj', 'psswd123', 'Dept'),
		('Dean Doe', 'dean', 'psswd123', 'none');

INSERT INTO patients(NAME, password) VALUES ('John Smith', 'pass123');

INSERT INTO booking (dtime, pid, username)
VALUES 	('2020-06-02 11:30:00','1','alice'),
		('2020-06-02 12:30:00','1','bob'),
		('2020-07-02 11:30:00','1','dean');






