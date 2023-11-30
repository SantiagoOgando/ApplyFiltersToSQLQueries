<h1>Apply Filters to SQL Queries</h1>

<h2>Project Description</h2>
I am a security professional at a large organization. Part of my job is to investigate security issues to help keep the system secure. I recently discovered some potential security issues that involve login attempts and employee machines.
My task is to examine the organization’s data in their employees and log_in_attempts tables. I’ll need to use SQL filters to retrieve records from different datasets and investigate the potential security issues.

<br />

<h2>Retrieve after hours failed login attempts:</h2>
There was a potential security incident that occurred after business hours (after 18:00). All after
hours login attempts that failed need to be investigated.
The following code demonstrates how I created a SQL query to filter for failed login attempts
that occurred after business hours.


SELECT * 
FROM log_in_attempts
WHERE login_time > ‘18:00’ AND SUCCESS = FALSE;

By selecting “*” we retrieve all the information from the log_in_attempts table with the conditions of unsuccessful logins occurring after 6:00pm.


<h2>Retrieve login attempts on specific dates:</h2>
A suspicious event occurred on 2022-05-09. Any login activity that happened on 2022-05-09
or on the day before needs to be investigated.

The following code demonstrates how I created a SQL query to filter for login attempts that
occurred on specific dates.


SELECT *
-> FROM log_in_attempts
-> WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';

I started by getting all the data from the log_in_attempts table. Then, I used a WHERE clause with an OR operator to show only login attempts from either 2022-05-09 or 2022-05-08. The first condition, login_date = '2022-05-09', filters logins on that date. The second one, login_date = '2022-05-08', is for logins on that date.

<h2>Retrieve login attempts outside of Mexico:</h2>
After investigating the organization’s data on login attempts, I believe there is an issue with the login attempts that occurred outside of Mexico. These login attempts should be investigated. 

The following code demonstrates how I created a SQL query to filter for login attempts that occurred outside of Mexico.


SELECT *
FROM log_in_attempts
WHERE NOT Country LIKE “MEX%”;

The query I used fetches login attempts from countries excluding Mexico. I began by selecting all information from the log_in_attempts table. Next, I employed a WHERE clause with NOT to exclude occurrences in Mexico. To achieve this, I utilized LIKE with the pattern MEX%, accommodating both 'MEX' and 'MEXICO' representations. The % symbol indicates any number of unspecified characters when combined with LIKE.

<h2>Retrieve employees in Marketing:</h2>
My team wants to update the computers for certain employees in the Marketing department.
To do this, I have to get information on which employee machines to update.

The following code demonstrates how I created a SQL query to filter for employee machines
from employees in the Marketing department in the East building.


SELECT *
FROM employees
WHERE department = “marketing” AND office LIKE “East%”;


The query I used extracts employees from the Marketing department situated in the East building. I kicked off by selecting all details from the employees table. Following that, I implemented a WHERE clause with AND to pinpoint employees in both the Marketing department and the East building. To accomplish this, I leveraged LIKE with East% as the pattern since the office column represents the East building along with the specific office number. The first condition, department = 'Marketing', filters Marketing department employees, while the second one, office LIKE 'East%', targets employees in the East building.


<h2>Retrieve employees in Finance or Sales:</h2>
The machines for employees in the Finance and Sales departments also need to be updated.
Since a different security update is needed, I have to get information on employees only from
these two departments.

The following code demonstrates how I created a SQL query to filter for employee machines
from employees in the Finance or Sales departments.


SELECT *
FROM employees
WHERE department = “sales” OR department = “finance”;

The query I've crafted gathers employees from both the Finance and Sales departments, as depicted in the initial part of the query. My approach began by selecting all information from the employees table. Subsequently, I incorporated a WHERE clause with OR to target employees present in either the Finance or Sales departments. I opted for the OR operator rather than AND because I intend to capture all employees affiliated with either department. The initial criterion, department = 'Finance', is tailored to filter Finance department employees. The subsequent criterion, department = 'Sales', effectively narrows the focus to employees associated with the Sales department.

<h2>Retrieve all employees not in IT:</h2>
My team needs to make one more security update on employees who are not in the
Information Technology department. To make the update, I first have to get information on
these employees.
The following demonstrates how I created a SQL query to filter for employee machines from
employees not in the Information Technology department.

SELECT *
FROM employees
WHERE NOT department = “Information Technology”;

The query I've constructed retrieves employees who are not part of the Information Technology department. To achieve this, I began by selecting all available data from the employees table. I then implemented a WHERE clause with NOT to accurately pinpoint employees who are not affiliated with this specific department.

<h2>Summary:</h2>
I utilized filtering techniques in SQL queries to extract targeted details about login attempts and employee machines. Two distinct tables, "log_in_attempts" and "employees," were employed. Employing operators such as AND, OR, and NOT, I effectively refined the results to match the specific requirements of each task. Additionally, I harnessed the power of the LIKE operator coupled with the wildcard symbol (%) to identify patterns in the data.



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
