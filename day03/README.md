# Answers

## Exercise 1

### Create Tables

`CREATE SCHEMA Institute; USE Institute;`

`CREATE TABLE Coach ( id INT NOT NULL, name char(30), mail char(30) NOT NULL, phone char(13), from_date date, hourly_rate INT, institute text, PRIMARY KEY (id) )`

`CREATE TABLE Types ( type_name VARCHAR(30), description VARCHAR(255), PRIMARY KEY (type_name) );`

`CREATE TABLE Coaches ( coach_id INT, type_name VARCHAR(30), FOREIGN KEY (coach_id) REFERENCES Coach (id), FOREIGN KEY (type_name) REFERENCES Types (type_name) );`

`CREATE TABLE Clients ( client_id INT, name VARCHAR(30), address VARCHAR(30), phone VARCHAR(30), PRIMARY KEY (client_id) )`

`CREATE TABLE Training_sequence ( client_id INT, start_date DATE, coach_id INT, type_name VARCHAR(30), hours DOUBLE, FOREIGN KEY (client_id) REFERENCES Clients (client_id), FOREIGN KEY (coach_id) REFERENCES Coaches (coach_id), FOREIGN KEY (type_name) REFERENCES Types (type_name) )`

### Insert Information

`INSERT INTO Coach VALUES (1, "Derrick", "derrick@gmail.com", "0544567865", "2008-11-11", 70, "Veitzman"), (2, "Rob", "rob@hotmail.com", "05445678654", "2020-11-11", 40, "Technion"), (3, "Rick", "rick@gmail.co.il", "054322546753", "2008-12-12", 60, "Tel Aviv"), (4, "Nick", "nick@gmail.com", "0534545643", "2008-11-11", 75, "Beer Sheva")`

`INSERT INTO Types VALUES ("Computer Science", "Work with computers and stuff"), ("Maths", "Numbers and that"), ("Politics", "Boring anoyying stuff and lying"), ("Football", "Fun sport")`

`INSERT INTO Coaches VALUES (1, "Computer Science"), (1, "Maths"), (2, "Maths"), (3, "Football"), (3, "Politics"), (4, "Maths"), (4, "Computer Science"), (4, "Politics")`

`INSERT INTO Clients VALUES (1, "Amir", "Zanzibar 4", "05465346754"), (2, "Rima", "Zpoona 7", "0434545653"), (3, "Dana", "Bagel 5", "065443456"), (4, "Hans", "Boo Nam 88", "05456654543")`

`INSERT INTO Training_sequence VALUES (1, "2020-11-11", 2, "Maths", 2), (1, "2020-11-12", 1, "Computer Science", 2), (2, "2020-11-11", 4, "Maths", 1), (2, "2020-11-12", 4, "Maths", 1), (2, "2020-11-13", 4, "Computer Science", 2), (3, "2020-11-11", 3, "Politics", 1), (3, "2020-11-11", 3, "Football", 1), (4, "2020-11-11", 2, "Maths", 2), (4, "2020-11-12", 1, "Maths", 1)`

### Create View of Client Money to Pay

`CREATE VIEW id_money as WITH Client_Coach_Hours as ( SELECT client_id, coach_id, hours FROM Training_sequence ), Coach_Pay as ( SELECT id, hourly_rate FROM Coach ) SELECT Client_Coach_Hours.client_id, sum(Client_Coach_Hours.hours * Coach_Pay.hourly_rate) as Money FROM Coach_Pay JOIN Client_Coach_Hours ON Coach_Pay.id = Client_Coach_Hours.coach_id GROUP BY Client_Coach_Hours.client_id`

`CREATE VIEW Client_Money as SELECT name, address, phone, id_money.Money FROM Clients JOIN id_money ON Clients.client_id = id_money.client_id`

## Exercise 2
