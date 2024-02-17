```mySQL
CREATE DATABASE IF NOT EXISTS organization;
USE organization;

CREATE TABLE Workers(
    worker_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    first_name CHAR(25),
    last_name CHAR(25),
    salary INT(15),
    joining_date DATE,
    department CHAR(25)
);

INSERT INTO Workers (first_name, last_name, salary, joining_date, department)
VALUES
    ('John', 'Doe', 50000, '2023-01-15', 'HR'),
    ('Jane', 'Smith', 60000, '2023-02-20', 'Finance'),
    ('Michael', 'Johnson', 55000, '2023-03-10', 'IT'),
    ('Emily', 'Williams', 52000, '2023-04-05', 'Marketing'),
    ('David', 'Brown', 58000, '2023-05-12', 'HR'),
    ('Sarah', 'Davis', 53000, '2023-06-18', 'IT'),
    ('Robert', 'Miller', 57000, '2023-07-22', 'Finance'),
    ('Jennifer', 'Wilson', 54000, '2023-08-30', 'Marketing');

CREATE TABLE Bonuses(
    worker_id INT,
    bonus_amount INT(10),
    bonus_date DATE,
    FOREIGN KEY (worker_id)
    REFERENCES Workers (worker_id)
    ON DELETE CASCADE
);

INSERT INTO Bonuses (worker_id, bonus_amount, bonus_date)
VALUES
    (1, 1000, '2023-05-01'),
    (2, 1500, '2023-06-15'),
    (3, 1200, '2023-07-10'),
    (4, 800, '2023-08-05'),
    (5, 2000, '2023-09-20'),
    (6, 1700, '2023-10-12');


CREATE TABLE Titles(
    worker_id INT,
    title CHAR(25),
    affected_from DATE,
    FOREIGN KEY (worker_id)
    REFERENCES Workers(worker_id)
    ON DELETE CASCADE
);

INSERT INTO Titles (worker_id, title, affected_from)
VALUES
    (1, 'Manager', '2023-01-15'),
    (2, 'Analyst', '2023-02-20'),
    (3, 'Developer', '2023-03-10'),
    (4, 'Coordinator', '2023-04-05'),
    (5, 'Supervisor', '2023-05-12'),
    (6, 'Designer', '2023-06-18'),
    (7, 'Engineer', '2023-07-22'),
    (8, 'Consultant', '2023-08-30');

SELECT * FROM Workers;

SELECT * FROM Workers WHERE salary > 10000;

SELECT * FROM Workers WHERE department = 'HR';

SELECT * FROM Workers WHERE salary BETWEEN 60000 AND 10000;

SELECT * FROM Workers WHERE department = 'IT' OR department = 'HR';

SELECT * FROM Workers WHERE department IN ('HR','IT');

```

