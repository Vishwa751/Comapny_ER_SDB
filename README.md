CREATE TABLE Employee (
    emp_id      INT PRIMARY KEY,
    first_name  VARCHAR(50),
    last_name   VARCHAR(50),
    birth_date  DATE,
    salary      DECIMAL(10,2),
    sex         CHAR(1),
    supervisor  INT REFERENCES Employee(emp_id)
);

CREATE TABLE Branch (
    branch_id   INT PRIMARY KEY,
    branch_name VARCHAR(100),
    mgr_id      INT REFERENCES Employee(emp_id)
);

CREATE TABLE Client (
    client_id   INT PRIMARY KEY,
    client_name VARCHAR(100),
    branch_id   INT REFERENCES Branch(branch_id)
);

CREATE TABLE Project (
    proj_id     INT PRIMARY KEY,
    proj_name   VARCHAR(100),
    location    VARCHAR(100),
    budget      DECIMAL(15,2)
);

CREATE TABLE Branch_Supplier (
    branch_id       INT REFERENCES Branch(branch_id),
    supplier_name   VARCHAR(100),
    supply_type     VARCHAR(100),
    PRIMARY KEY (branch_id, supplier_name)
);

CREATE TABLE Works_On (
    emp_id      INT REFERENCES Employee(emp_id),
    proj_id     INT REFERENCES Project(proj_id),
    hours       DECIMAL(5,2),
    PRIMARY KEY (emp_id, proj_id)
);

CREATE TABLE Works_With (
    emp_id      INT REFERENCES Employee(emp_id),
    client_id   INT REFERENCES Client(client_id),
    sales       DECIMAL(10,2),
    PRIMARY KEY (emp_id, client_id)
);
