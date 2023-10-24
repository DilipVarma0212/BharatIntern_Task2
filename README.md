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


INSERT INTO Titanic command as follow:

    INSERT INTO Titanic (PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, Embarked) 
    VALUES
    (892, 0, 3, 'Kelly, Mr. James', 'male', 34.5, 0, 0, '330911', 7.8292, NULL, 'Q'),
    (893, 1, 3, 'Wilkes, Mrs. James (Ellen Needs)', 'female', 47, 1, 0, '363272', 7.0, NULL, 'S'),
    (894, 0, 2, 'Myles, Mr. Thomas Francis', 'male', 62, 0, 0, '240276', 9.6875, NULL, 'Q'),
    (895, 0, 3, 'Wirz, Mr. Albert', 'male', 27, 0, 0, '315154', 8.6625, NULL, 'S'),
    (896, 1, 3, 'Hirvonen, Mrs. Alexander (Helga E Lindqvist)', 'female', 22, 1, 1, '3101298', 12.2875, NULL, 'S'),
    (897, 0, 3, 'Svensson, Mr. Johan Cervin', 'male', 14, 0, 0, '7538', 9.225, NULL, 'S'),
    (898, 1, 3, 'Connolly, Miss. Kate', 'female', 30, 0, 0, '330972', 7.6292, NULL, 'Q'),
    (899, 0, 2, 'Caldwell, Mr. Albert Francis', 'male', 26, 1, 1, '248738', 29.0, NULL, 'S'),
    (900, 1, 3, 'Abrahim, Mrs. Joseph (Sophie Halaut Easu)', 'female', 18, 0, 0, '2657', 7.2292, NULL, 'C'),
    (901, 0, 3, 'Davies, Mr. John Samuel', 'male', 21, 2, 0, 'A/4 48871', 24.15, NULL, 'S'),
    (902, 0, 3, 'Ilieff, Mr. Ylio', 'male', NULL, 0, 0, '349220', 7.8958, NULL, 'S'),
    (903, 0, 1, 'Jones, Mr. Charles Cresson', 'male', 46, 0, 0, '694', 26.0, NULL, 'S'),
    (904, 1, 1, 'Snyder, Mrs. John Pillsbury (Nelle Stevenson)', 'female', 23, 1, 0, '21228', 82.2667, 'B45', 'S'),
    (905, 0, 2, 'Howard, Mr. Benjamin', 'male', 63, 1, 0, '24065', 26.0, NULL, 'S'),
    (906, 1, 1, 'Chaffee, Mrs. Herbert Fuller (Carrie Constance Toogood)', 'female', 47, 1, 0, 'W.E.P. 5734', 61.175, 'E31', 'S'),
    (907, 1, 2, 'del Carlo, Mrs. Sebastiano (Argenia Genovesi)', 'female', 24, 1, 0, 'SC/PARIS 2167', 27.7208, 'C', 'C'),
    so on....


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

