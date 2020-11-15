-- Employee Datebase 
DROP TABLE employees

CREATE TABLE employees (
	emp_no INT NOT NULL,
	emp_title_id VARCHAR NOT NULL,
	birth_date DATE NOT NULL,
	first_name VARCHAR (20) NOT NULL,
	last_name VARCHAR (20) NOT NULL,
	sex VARCHAR (2) NOT NULL,
	hire_date DATE NOT NULL,
	CONSTRAINT pk_Employees PRIMARY KEY (
        emp_no)
);

select * from employees;

DROP TABLE departments;

CREATE TABLE departments (
    "dept_no" VARCHAR NOT NULL,
    "dept_name" VARCHAR NOT NULL,
    CONSTRAINT pk_departments PRIMARY KEY (dept_no)
);

select * from departments

DROP TABLE dept_manager;

CREATE TABLE dept_manager (
	dept_no VARCHAR(5) NOT NULL,
    emp_no INT NOT NULL
);

select * from dept_manager;


DROP TABLE dept_emp;

CREATE TABLE dept_emp (
    emp_no INT NOT NULL,
    dept_no VARCHAR NOT NULL
);

select * from dept_emp;

DROP TABLE titles;

CREATE TABLE titles (
	title_id VARCHAR NOT NULL, 
	title VARCHAR NOT NULL,
	CONSTRAINT pk_Titles PRIMARY KEY (title_id)
);

select * from titles;




DROP TABLE salaries;
CREATE TABLE salaries (
	emp_no INT NOT NULL, 
	salary INT NOT NULL,
	CONSTRAINT pk_Salaries PRIMARY KEY (emp_no)
);

select * from salaries;


ALTER TABLE "dept_emp" ADD CONSTRAINT "fk_Dept_emp_emp_no" FOREIGN KEY("emp_no")
REFERENCES "employees" ("emp_no");

ALTER TABLE "dept_emp" ADD CONSTRAINT "fk_Dept_emp_dept_no" FOREIGN KEY("dept_no")
REFERENCES "departments" ("dept_no");

ALTER TABLE "employees" ADD CONSTRAINT "fk_Employees_emp_title_id" FOREIGN KEY("emp_title_id")
REFERENCES "titles" ("title_id");

ALTER TABLE "dept_manager" ADD CONSTRAINT "fk_dept_manager_dept_no" FOREIGN KEY("dept_no")
REFERENCES "departments" ("dept_no");

ALTER TABLE "dept_manager" ADD CONSTRAINT "fk_Dept_manager_emp_no" FOREIGN KEY("emp_no")
REFERENCES "employees" ("emp_no");

ALTER TABLE "salaries" ADD CONSTRAINT "fk_Salaries_emp_no" FOREIGN KEY("emp_no")
REFERENCES "employees" ("emp_no");
