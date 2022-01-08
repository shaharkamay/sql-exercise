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

### Create Tables

`CREATE SCHEMA Disasters; USE Disasters;`

`CREATE TABLE Event ( etype char(30), description text, PRIMARY KEY (etype) )`

`CREATE TABLE City ( cname char(30), country char(30), population INT, PRIMARY KEY (cname) )`

`CREATE TABLE City ( cname char(30), country char(30), population INT, PRIMARY KEY (cname) )`

`CREATE TABLE Disaster ( cname char(30), year INT, etype char(30), casualties INT, FOREIGN KEY (cname) REFERENCES City (cname), FOREIGN KEY (etype) REFERENCES Event (etype) )`

`CREATE TABLE Prediction ( cname char(30), etype char(30), casualties INT, FOREIGN KEY (cname) REFERENCES City (cname), FOREIGN KEY (etype) REFERENCES Event (etype) )`

`CREATE TABLE Measures ( etype char(30), provider char(30), cost INT, precent INT, FOREIGN KEY (etype) REFERENCES Event (etype), CHECK (precent BETWEEN 0 AND 101) )`

### Insert Information

`INSERT INTO Event VALUES ("earthquake", "from 5 in Richter scale"), ("fire", "burning that produces flames that send out heat and light and sometimes smoke"), ("flood", "overflowing of a large amount of water over what is normally dry land"), ("tornado", "funnel-shaped vortex of violently rotating winds advancing beneath a large storm system"), ("volcano", "lava, ash, rock and gasses eruption")`

`INSERT INTO City VALUES ("Hilo", "Hawaii", 43000), ("Kagoshima", "Japan", 700000), ("Naples", "Italy", 3000000), ("Pasto", "Columbia", 450000), ("Tsfat", "Israel", 3600)`

`INSERT INTO Disaster VALUES ("Hilo", 1903, "volcano", 500), ("Hilo", 1914, "volcano", 300), ("Hilo", 1926, "volcano", 20), ("Hilo", 1971, "tornado", 85), ("Hilo", 1984, "volcano", 50), ("Hilo", 1989, "tornado", 50), ("Hilo", 2002, "tornado", 5), ("Hilo", 2011, "tornado", 70), ("Hilo", 2015, "tornado", 50), ("Kagoshima", 1914, "earthquake", 35), ("Kagoshima", 1915, "volcano", 100), ("Kagoshima", 1974, "volcano", 50), ("Kagoshima", 1993, "flood", 2600), ("Kagoshima", 2017, "volcano", 20), ("Naples", 1906, "volcano", 50), ("Naples", 1944, "volcano", 35), ("Naples", 1979, "volcano", 50), ("Naples", 1998, "flood", 200), ("Pasto", 1988, "volcano", 30), ("Pasto", 1993, "volcano", 45), ("Pasto", 2002, "volcano", 15), ("Pasto", 2008, "volcano", 30), ("Pasto", 2010, "volcano", 30), ("Pasto", 2018, "flood", 15), ("Tsfat", 1837, "earthquake", 5000)`

`INSERT INTO Prediction VALUES ("Hilo", "flood", 100), ("Hilo", "tornado", 400), ("Kagoshima", "fire", 320), ("Naples", "volcano", 50), ("Pasto", "tornado", 200), ("Pasto", "volcano", 500), ("Tsfat", "earthquake", 1000)`

`INSERT INTO Measures VALUES ("flood", "fire department", 1000000, 60), ("tornado", "army", 300000, 20), ("tornado", "police", 400000, 50), ("volcano", "army", 600000, 90), ("volcano", "fire department", 500000, 85), ("volcano", "police", 200000, 70)`

### Create View

`SELECT cname, COUNT(cname) as disasters_count FROM Disaster WHERE (2021 - year) <= 50 GROUP BY cname ORDER BY disasters_count DESC LIMIT 1;`

`create view predict_death as select cname as ct, sum(casualties) as total_death from prediction group by ct`

`create view Safety_rank as select cname, population, total_death, ((total_death/population)*100) as safety_rate from city c JOIN predict_death p on(c.cname = p.ct)`
