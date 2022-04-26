# SQL_queries

--creating the EMPLOYEE TABLE

CREATE TABLE Employee(
    emp_id INT PRIMARY KEY,
    first_name VARCHAR(40),
    last_name VARCHAR(40),
    birth_day DATE,
    sex VARCHAR(1),
    salary INT ,
    supaer_id INT,
    branch_id INT
);

--creating a branch table

CREATE TABLE branch(
    branch_id INT PRIMARY KEY,
    branch_name VARCHAR(40),
    mrg_id INT,
    mrg_start_daY DATE,
    FOREIGN KEY (mrg_id)REFERENCES Employee(emp_id) ON DELETE SET NULL
);

--checking to see what the table looks like 

DESCRIBE branch;

--creating a client table

CREATE TABLE client(
    client_id INT PRIMARY KEY,
    client_name VARCHAR(40),
    branch_id INT,
    FOREIGN KEY (branch_id) REFERENCES branch(branch_id) ON DELETE SET NULL
);

--creating a table that that shows the employees that work with a particular client 

CREATE TABLE Works_with(
    emp_id INT,
    client_id INT,
    total_sales INT,
    PRIMARY KEY(emp_id, client_id),
    FOREIGN KEY(emp_id) REFERENCES Employee(emp_id) ON DELETE CASCADE,
    FOREIGN KEY(client_id) REFERENCES client(client_id) ON DELETE CASCADE
);

--creating a table for the branch suppliers

CREATE TABLE Branch_supplier(
    Branch_id INT,
    supplier_name VARCHAR(40),
    supplier_type VARCHAR(40),
    PRIMARY KEY(branch_id, supplier_name),
    FOREIGN KEY (branch_id) REFERENCES branch(branch_id) ON DELETE CASCADE
);

--adding an another column to the employee table

ALTER TABLE Employee
ADD FOREIGN KEY(branch_id)
REFERENCES Branch(branch_id)
ON DELETE SET NULL;
	
ALTER TABLE Employee
ADD FOREIGN KEY(super_id)
REFERENCES Employee(emp_id)
ON DELETE SET NULL;

--inserting values to the employee and branch table with branch id 1

INSERT INTO Employee VALUES(100, 'david', 'Wallace', '1967-11-17', 'm', 250000, NULL, NULL );
INSERT INTO branch VALUES(1, 'Corporation', 100, '2006-02-09');

UPDATE Employee
SET branch_id = 1
WHERE emp_id = 100;

INSERT INTO Employee VALUES('101', 'JAN', 'LEVISON', '1961-05-11', 'F', 110000, 100, 1);

--inserting values to the employee and branch table with branch id 2

INSERT INTO Employee VALUES(102, 'Micheal', 'scott', '1964-03-15', 'm', 75000, 100, NULL );
INSERT INTO branch VALUES(2, 'scranton', 102, '1992-04-06');

UPDATE Employee
SET branch_id = 2
WHERE emp_id = 102;

INSERT INTO Employee VALUES('103', 'Angela', 'Martin', '1971-06-25', 'F', 63000, 102, 2);
INSERT INTO Employee VALUES('104', 'Kelly', 'Kapoor', '1980-02-05', 'F', 55000, 102, 2);
INSERT INTO Employee VALUES('105', 'Stanley', 'Hudson', '1958-02-19', 'M', 69000, 102, 2);

--inserting values to the employee and branch table with branch id 3

INSERT INTO Employee VALUES(106, 'Josh', 'Porter', '1969-09-05', 'M', 78000, 100, NULL );
INSERT INTO branch VALUES(3, 'stanford', 106, '1998-02-13');

UPDATE Employee
SET branch_id = 3
WHERE emp_id = 106;

INSERT INTO Employee VALUES('107', 'Andy', 'Bernard', '1973-07-22', 'M', 65000, 106, 3);
INSERT INTO Employee VALUES('108', 'Jim', 'HALPERT', '1978-10-01', 'M', 71000, 106, 3);

--inserting values to the supplier taable

SUPPLIER
INSERT INTO Branch_supplier VALUES(2, 'Hammer Mill', 'paper');
INSERT INTO Branch_supplier VALUES(2, 'Uni-ball', 'Writing Utensils');
INSERT INTO Branch_supplier VALUES(3, 'Patriot paper', 'paper');
INSERT INTO Branch_supplier VALUES(2, 'J.T form & label', 'Custom Form');
INSERT INTO Branch_supplier VALUES(3, 'Uni-ball', 'Writing Utensils');
INSERT INTO Branch_supplier VALUES(3, 'Hammer Mill', 'paper');
INSERT INTO Branch_supplier VALUES(3, 'Stanford Lables', 'Custom Form');

--inserting values to the CLIENT TABLE 

INSERT INTO client VALUES(400, 'Dunmore Highschool' ,2);
INSERT INTO client VALUES(401, 'Lackwana Country' ,2);
INSERT INTO client VALUES(402, 'FedEx' ,3);
INSERT INTO client VALUES(403, 'John Daly Law, LLC' ,3);
INSERT INTO client VALUES(404, 'Scranton Whitepages' ,2);
INSERT INTO client VALUES(405, 'Times Newspaper' ,3);
INSERT INTO client VALUES(406, 'FedEx' ,2);

--returning queries whether they true or not

select E.first_name, E.last_name, W.total_sales
FROM EMPLOYEE E
LEFT JOIN works_with W
     ON E.emp_id = W.emp_id
     WHERE E.emp_id = W.emp_id
;

--Combining queries 

select first_name
FROM EMPLOYEE
UNION
SELECT client_name
FROM Client
;


