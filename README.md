# RetailAnalitycs v2.0 Web

Web interface creation for SQL3 project in Python.


## Contents

1. [Chapter I](#chapter-i) \
    1.1. [Introduction](#introduction)
2. [Chapter II](#chapter-ii) \
    2.1. [Rules](#rules) \
    2.2. [Information](#information)
3. [Chapter III](#chapter-iii) \
    3.1. [Part 1. Implementing a web application for the SQL3 project](#part-1-implementing-a-web-application-for-the-sql3-project)  \
    3.2. [Part 2. Authorization](#part-2-authorization)  \
    3.3. [Part 3. Logging](#part-3-logging)  \
    3.4. [Part 4. Bonus. Preparing for deployment](#part-4-bonus-preparing-for-deployment) \
    3.5. [Part 5. Bonus. SPA-frontend](#part-5-bonus-spa-frontend)


## Chapter I



## Introduction

In this project you will implement a web interface for the SQL3 project. You will improve your knowledge of the Python programming language, MVC pattern and the basics of Web application development, as well as get familiar with ORM frameworks and use them in your work. The application should support CRUD operations, table import/export, authorization, GUI operations/functions developed in the previous step, and logging of user actions. 


## Chapter II

## Rules 

- The database model view, as well as procedures related to adding/removing/correcting data, are in the SQL3 project
- Your solution must be in the git repository for evaluation
- Do you have a question? Ask your neighbor to the right. Otherwise, try your neighbor to the left
- Your reference guide: colleagues / Internet / Google

## Information

### ORM

**ORM (Object-Relational Mapping)** is a programming technology that links databases with the concepts of object-oriented programming languages, creating a "virtual object database". \
In other words, an ORM is a set of classes that adds another layer of abstraction to the tables stored in the database. This abstraction allows you to work with database objects as objects of the programming language you use, i.e., to work with data in terms of classes rather than data tables. 

Model classes, fields and entity instances are all mapped to the database concept.

| Term | Compliance |
| ------- | -------- |
| model class | table in the database |
| field | column in a table |
| entity instance | string in a table |

Within the ORM there are 2 approaches: *Code first* and *Model/Database first*.

In **Code first** you write the entity classes first and the database schemas are aligned to the new code state. Any database undergoes changes during its lifetime: new tables are added, old ones are deleted, and some are changed. Changes in the database are performed with the help of the migration mechanism. **Migration** is a description of changes you want to make to the database tables. 

In **Model first** you develop or change the database first (by executing SQL queries or forming queries using ORM tools), and the entities are generated from it. For example, to add a new field, just add a new column.

It is reasonable to use ORM in large projects that use databases, but some programmers prefer to generate the necessary SQL queries themselves to improve the query execution speed. The reason is that in the case of complex queries ORM does not always generate the best SQL-queries to the database, which in the case of a large sample is very important, especially if the sample is more than one table.

ORM systems are present in any large framework - Laravel, Entity Framework Core, Django ORM, SQLAlchemy.


## Chapter III

You need to implement a web application for the SQL3 project

## Part 1. Implementing a web application for the SQL3 project

### General requirements

- The program must be developed in Python 3.11
- The program code must be placed in the src folder
- It is necessary to follow Google Code Style when writing the code
- The web application must be developed
- The application must be implemented using MVC framework (Django or flask)
- The program must be implemented using **MVC** pattern, and 
    - there should be no business logic code in the view code;
    - there must be no interface code in the controller and model;
    - controllers must be thin;
- Perform page rendering on the server side (using **Server-Side Rendering** technology)
- You need to completely reuse the database from the SQL3 project, including it in the Model component (while using the ORM *ORM Django или SQLAlchemy* in Model/Database First mode)
- The application design must be intuitive 

### Content requirements

- The main page must contain:
    - A navigation menu that provides access to the main sections of the application: *"Data"* and *"Offerings"*.
    - An *"About"* field, which contains basic information about the student who completed the project

- The graphical shell of *"Data"* and *"Proposals"* sections should contain the following sections:
    - A header that, when clicked, will take you to the home page
    - The navigation menu, which allows to navigate through the main sections
    - The content part of the section
    - A navigation panel enabling navigation through subsections of the selected section (if necessary)

- The *"Data"* section should contain sub-sections allowing supporting the following functionality through the GUI
    - Carry out CRUD operations on all tables
    - At any modification of tables (create, update, delete) the application must ask the user to confirm the operation
    - After any kind of modification of tables the modified table must be displayed to the user
    - Import and export data for each table from/to files with the *.csv* extension

- The section *"Suggestions"* must contain subsections that allow supporting the following functionality through GUI
    - Implement the ability to calculate all the personalized offers and export them to a .csv file
    - When carrying out calculations it is necessary to call functions implemented in the database
    - If you need to enter parameters to perform a procedure or function, the graphical interface should provide a form for entering data
    - If the entered arguments are incorrect, the application should handle such a situation (display an error message about the incorrectness of the entered data and offer to try again)

- The application must be configured by means of a configuration file that includes a DBMS connection string

## Part 2. Authorization

It is necessary to implement user authorization. 

The application must support 2 roles: *administrator* and *visitor* and grant certain rights according to the role: 

### Administrator

- The administrator has full rights to edit and view
any information, start and stop the processing.

### Visitor

- Only view information from all tables.

If the data were incorrect, the application should handle such a situation (give an error about the incorrectness of the entered data and offer to try again). 

## Part 3. Logging

It is necessary to implement logging of all user's actions (log files are to be written in the logs folder). Every day a new logs file is created. The name of the files must correspond to the template *logs_dd-MM-yy-h-mm-ss*.

Each log must have its level of importance marked:
- **Info**: expected event;
- **Warning**: unexpected events that allow the application to continue running;
- **Error**: an event that prevents the program from continuing;

## Part 4. Bonus. Preparing for deployment

Prepare the application to run.
To do this, you need to pack in docker containers:
- database
- proxy server (use nginx)
- web applications

Prepare docker-compose to start the entire application. Only the docker-container containing Nginx must look "outside". 

## Part 5. Bonus. SPA-frontend

Implement the SPA-frontend in any component framework (Vue/React/Angular).

