---
title: "MySQL and Flask Tutorial"
created: 2021-02-26
date: 2021-02-26
categories: 
  - python
tags: 
  - flask
  - mysql
  - python
authors: 
  - thecd
description: "How to use MySQL in Python using Flask. MySQL databases are common on the web and very easy to setup in Python using Flask."
cover:
    image: images/mysql-in-python-flask.png
url: "/use-mysql-in-python-flask"
---

It's common when building a backend to access a database for API's and other situations. Luckily with Python, there is an easy module for accessing a MySQL database to make queries. This post will show you how to use **MySQL in Flask** so that you can use databases in your app easily.

## Install MySQL Package for Python Flask

To install the required Python package for working with a MySQL database in Flask, we will use "pip". I recommend doing this from a virtual environment, if you need help with that check out my post on setting up a [Python Virtual Environment](https://credibledev.com/install-virtualenv-on-arch-linux-for-python/). The package that we want to install is called, **flask-mysql-connector**. This package will handle the communication between Flask and the MySQL database.

```
pip install flask-mysql-connector
```

Next, we need to set up some environment variables to store the connection information.

Check out our post on [setting up a Python Flask app on a production LiteSpeed Server](https://credibledev.com/python-flask-dev-environment-on-manjaro-linux/).

## Install Python-DotEnv

We want to install the **python-dotenv** package so we can store our MySQL variables outside of our code. By storing our MySQL database connection details in a separate file provides a bit more security and gives us a central place to edit them in the future.

```
pip install python-dotenv
```

Once this is installed, now we can create a .env file to hold these important variables to later access within our code. In your .env file include the lines below, replacing the values with your database details:

```
DBHOST=localhost
DBNAME=database_name
DBUSER=username
DBPASS=password
```

## Connect to a MySQL Database using Python Flask

![flask mysql](images/flask-mysql.png)

Now inside our Flask app where we want to connect to the MySQL database, we need to add a few imports at the top as follows. We will first import the dotenv and os packages so we can access our MySQL variables in the .env file. Next, we will import the flask mysql package to handle the MySQL database communication.

```
from dotenv import load_env
import os
from flask_mysql_connector import MySQL
```

Now that we have the imports taken care of, we can make a connection and query.

First, let's pull in the variables we created in the .env file.

```
app.config['MYSQL_USER'] = os.getenv('DBUSER')
app.config['MYSQL_DATABASE'] = os.getenv('DBNAME')
app.config['MYSQL_HOST'] = os.getenv('DBHOST')
app.config['MYSQL_PASSWORD'] = os.getenv('DBPASS')
```

Next, we will initialize MySQL into our app by calling MySQL and passing in our app.

```
mysql = MySQL(app)
```

Now we have our variables set up and MySQL initialized in our app, we can set up a query.

## Example MySQL Flask Query

Here we setup a sample query and tell Flask to connect with our MySQL database for the query.

```
SAMPLE_QUERY = 'select * from table_name where column_name="some_value"'

@app.route('/db_test')
def db_test():
    conn = mysql.connection
    cur = conn.cursor()
    cur.execute(SAMPLE_QUERY)
    output = cur.fetchall()
    return str(output)
```

Nice, you've made your first MySQL query from your Python Flask app! Congrats! You can navigate to http://localhost:5000/db\_test in your browser to see the output once you run your Flask app.

If you would like to know more or see a specific example, let me know in the comments!
