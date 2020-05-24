---
title: Learning Database
date: "2020-05-17T12:40:32.169Z"
description: What Database
---

# Database

one to one and one to many

```
Patient:

PatientID Name
--------- ----
1         John
2         Matt

Patient_Medication:

PrescriptionID PatientID Name
-------------- --------- ------------
1              1         Antacid
2              1         Paracetamol
3              2         Asthma inhaler
```

You are in a one to many relationship. Patient John can have multiple medications in prescription table

```
Patient:

PatientID Name
--------- ----
1         John
2         Matt
3         Katie

Medication:

MedicationID Name
------------ ----
1            Antacid
2            Paracetamol
3            Asthma inhaler

Patient_Medication:

ID  PatientID MedicationID
--- --------- ------------
1   1 (John)        1 (Antacid)
2   1 (John)        2 (Paracetamol)
3   2 (Matt)        3 (Asthma inhaler)
4   3 (Katie)       2 (Paracetamol)
5   3 (Katie)       3 (Asthma inhaler)
```

This situation is a many-to-many relationship where many patients can have many medications and vice versa. Usually Patient_Medication is called a junction table.

**One-to-Many**

One person has many sills. A skill is not reused between persons.

**Many-to-Many**

An Author can write several Books, and a Book can be written by several Authors.

### [Set Sail on Database Relationships: Understanding One-to-One, One-to-Many, and Many-to-Many](https://www.smartsheet.com/database-relationships)

Database become powerful by linking the data separate files

- you can link one book to another with the same author or categories
- Amazon can connect customers to the products they view and buy
- FBI can see comparable clues that link different crimes

### How does a database work?

- Each piece of data is entered into a field
  - ex) the title of a song on your favorite album and its composer
- Fields are combined to become records
  - ex) all the songs on the album, and everyone who wrote them
- Similar records are combined into a file
  - ex) vinyl collection, CD collection...
- Flat-File Databse
  - You can't see if you have Ariana Grande's No Tear No Cry on both vinyl and CD, or how many cover versions of The Beatles' Eleanor Rigby are in your collection unless you open and search each file.
  - It's useful if you don't have much data to manage.
- Relational Database
  - but if you want to compare the contents of each file, this is what you need.
  - It allows you to make connections between fields and records.
  - Instead of files, it has tables, a set of related data displayed in rows and columns to resemble a spreadsheet.

### What is a Database Table Relationship?

Primary and Foreign Keys

- Each record in a table has a unique identifier. It can be a single column (like a student ID number) or a combination of columns (date and time of file creation + the customers' last name).
- That identifier is called a key.
- Relationship
  - When a table references the data from another table
  - The key in the referenced table is called foreign key.
