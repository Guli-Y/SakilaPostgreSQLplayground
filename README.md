### 👋 If you want to practice your SQL and ETL skills, this is the repository you are looking for 

[Sakila](https://dev.mysql.com/doc/sakila/en/sakila-structure.html) is sample database in MySQL, and its PostgreSQL version is called Pagila. Here you will create the Pagila database locally on your computer using the following instructions. Using the Pagila database, you will have a chance to practice your SQL skills and write some ETL pipelines. The instruction here is written for WSL. If you have a different system, please adapt your code.

## 🐑 Create your Pagila Database locally

1. Fork the current repo and clone it locally on your computer (In case you don't know how to fork and clone a repo, follow [this](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo))


2. Fork [this](https://github.com/devrimgunduz/pagila) repo and clone it inside of your local SakilaPostgresplacground directory

    - Go to SakilaPostgreSQLplayground directory from your terminal and check whether you have pagila directory in it

3. Install postgresql

    - sudo apt-get remove postgresql                                         

    - sudo apt-get install postgresql

4. start the postgresql service

    - sudo service postgresql start

5. Create pagila database using psql:

    - sudo -u postgres psql     

    - postgres=# DROP DATABASE IF EXISTS pagiladb; 

    - postgres=# CREATE DATABASE pagiladb;                           

    - postgres=# \q                      

6. Set a new password for postgres user using psql:

    - sudo -u postgres psql                              

    - postgres=# \password postgres                    

    - -- enter new password ---       (you will use this password in next steps)               

    - postgres=# \q

7. Create schema using following command from terminal:

    - psql -U postgres -h 127.0.0.1 -d pagiladb -f pagila/pagila-schema.sql                                 

    - ----- enter password ------

8. Copy data into pagila database using following command from terminal:

    - psql -U postgres -h 127.0.0.1 -d pagiladb -f pagila/pagila-data.sql                          

    - ----- enter password -----

❗ All of these steps are only required for the first setup. After setup, if you want to access to the database again, you only need to run step 4 to start postgresql service and connect to the database with the following steps.

## 🐑🐑 Connect to your Pagila Database in jupyter notebook

Before starting the next setion, install jupyter notebook if you haven't yet. 

- From terminal: 

    - pip install jupyter notebook

👉 **ipython-sql** introduces a %sql (or %%sql) magic to your notebook allowing you to connect to a database

1. Install ipython-sql if you haven't done it before.

- From terminal: 
    - pip install ipython-sql
- In jupyter notebook: 
    - ! pip install ipython-sql

2. Load ipython-sql by running the following command in your jupyter notebook:

    - %load_ext sql

3. Connect to the Pagila database you created by running the following command in your jupyter notebook:

    - %sql postgresql://postgres:postgres_password\@127.0.0.1:5432/pagiladb            

    - ☝️  Don't forget to replace the 'postgres_password' with your own password to postgres


### 👏 Now, you are all set! To run a SQL query, you just need to put a %%sql magic on the first line of your cell.

> For example:

>> %%sql                                  
SELECT *              
FROM film                                                  
LIMIT 5;                      

❗ Remember that this database is a large database. To keep your notebook readable, use LIMIT to limit your query results.



### 🔥 Once you have built your Pagila Database locally, you can start with the guided challenges in playground.ipynb. 

### 🛠️ To save some time, you might find [this](https://raw.githubusercontent.com/LintangWisesa/Sakila_MySQL_Example/master/SampleSakila.png) Sakila Schema helpful


