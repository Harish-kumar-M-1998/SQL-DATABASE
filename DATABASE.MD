** DATABASE **
CREATE DATABASE GUVI;
TABLE CREATIONS:	
USE GUVI;
CREATE TABLE users (
    userid INT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    created_at TIMESTAMP
);
CREATE TABLE students (
    studentid INT PRIMARY KEY,
    userid INT,
    fullname VARCHAR(255) NOT NULL,
    phone INT NOT NULL,
  FOREIGN KEY (userid) REFERENCES users(userid)
);
CREATE TABLE mentors (
    mentorid INT PRIMARY KEY,
    userid INT,
    fullname VARCHAR(255) NOT NULL,
    phone INT NOT NULL,
    FOREIGN KEY (userid) REFERENCES users(userid)
);
CREATE TABLE topics (
    topicid INT PRIMARY KEY,
    topicname VARCHAR(255),
    description TEXT NOT NULL,
);
CREATE TABLE tasks (
    taskid INT PRIMARY KEY,
    topicid INT,
    taskname VARCHAR(255),
    description TEXT,
    due_date DATE,
    assigned_to INT,
    FOREIGN KEY (topicid) REFERENCES topics(topicid),
    FOREIGN KEY (assigned_to) REFERENCES users(userid)
);
CREATE TABLE attendance (
    attendanceid INT PRIMARY KEY,
    userid INT,
    date DATE,
    status VARCHAR(20),
    FOREIGN KEY (userid) REFERENCES users(userid)
);
