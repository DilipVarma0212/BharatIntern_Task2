# BharatIntern_Task2

Project Summary: This is the task of the Titanic dataset to build a model that predicts whether a passenger on the Titanic survived or not. Make a system which tells whether the person will be save from sinking. What factors were most likely lead to success-socio-economic status, age, gender and more.


TOOL USED: SQL Server Management Studio (Transact-SQL)


CREATE DATABASE BHARATINTERN command is as follow:

  create database BharatIntern
  

CREATE TABLE Titanic command as follow:

    create table Titanic
    (
    PassengerId int not null,
    Survived int not nul,
    Pclass int not nul,
    Name nvarchar(100) not null,
    Sex nvarchar(50) not null,
    Age float null,
    SibSp int not null,
    Parch int not null,
    Ticket nvarchar(50) not null,
    Fare money null,
    Cabin nvarchar(50) null,
    Embarked nvarchar(50) not null
    )


Retrive all the coloumns from the table Titanic:

    select * from Titanic;


Retrieve the number of passengers by male:

    select Sex, COUNT(*) as Total_male
    from Titanic
    where Sex = 'male'
    group by Sex;


Retrieve the number of passengers by female:

    select Sex, COUNT(*) as Total_female
    from Titanic
    where Sex = 'female'
    group by Sex;


Calculate the average age of passengers:

    SELECT AVG(Age) as AverageAge
    FROM Titanic;


Find the passengers with missing age values:

    SELECT *
    FROM Titanic
    WHERE Age IS NULL;


List the passengers in descending order of fare paid:

    SELECT *
    FROM Titanic
    ORDER BY Fare DESC;


Count the number of passengers in each passenger class (Pclass):

    SELECT Pclass, COUNT(*) as Count of Passenger
    FROM Titanic
    GROUP BY Pclass;


Retrieve passengers who survived (Survived=1) and their average age:

    SELECT Survived, AVG(Age) as AverageAge
    FROM Titanic
    WHERE Survived = 1
    GROUP BY Survived;


Find the passengers who embarked from 'S' and paid more than $50 as fare:

    SELECT *
    FROM Titanic
    WHERE Embarked = 'S' AND Fare > 50;


Calculate the total number of siblings/spouses (SibSp) and parents/children (Parch) on board:

    SELECT SUM(SibSp) as TotalSibSp, SUM(Parch) as TotalParch
    FROM Titanic;


Find the passengers who survived (Survived=1) and are in first class (Pclass=1):

    SELECT *
    FROM Titanic
    WHERE Survived = 1 AND Pclass = 1;


List passengers in descending order of age:

    SELECT *
    FROM Titanic
    ORDER BY Age DESC;


Retrieve the passengers with a cabin number recorded:

    SELECT *
    FROM Titanic
    WHERE Cabin IS NOT NULL;


Count the number of passengers who embarked from each port (Embarked):
    
    SELECT Embarked, COUNT(*) as Count
    FROM Titanic
    GROUP BY Embarked;
    

Calculate the average fare paid by passengers in each passenger class (Pclass):

    SELECT Pclass, AVG(Fare) as AvgFare
    FROM Titanic
    GROUP BY Pclass;


Find the passengers who are children (age less than 18) and were traveling with at least one parent (Parch > 0):

    SELECT *
    FROM Titanic
    WHERE Age < 18 AND Parch > 0;


Count the number of male and female passengers who survived:
  
    SELECT Sex, COUNT(*) as Count
    FROM Titanic
    WHERE Survived = 1
    GROUP BY Sex;


List passengers who paid more than twice the average fare:

    SELECT PassengerId, Name, Sex
    FROM Titanic
    WHERE Fare > 2 * (SELECT AVG(Fare) FROM Titanic);


Retrieve passengers with the same ticket number (possible families or groups traveling together):

    SELECT Ticket, COUNT(*) as GroupSize
    FROM Titanic
    GROUP BY Ticket
    HAVING COUNT(*) > 1;

