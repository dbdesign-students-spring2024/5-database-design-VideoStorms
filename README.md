# Data Normalization and Entity-Relationship Diagramming

An assignment to normalize the structure of data and establish a set of Entity-Relationship Diagrams for the data.

The contents of this file will be deleted and replaced with the content described in the [instructions](./instructions.md)

| assignment_id | student_id | due_date | professor      | assignment_topic          | classroom | grade | relevant_reading   | professor_email    |
|---------------|------------|----------|----------------|---------------------------|-----------|-------|--------------------|--------------------|
| 1             | 1          | 23.02.21 | Melvin         | Data normalization        | WWH 101   | 80    | Deumlich Chapter 3 | l.melvin@foo.edu   |
| 2             | 7          | 18.11.21 | Logston        | Single table queries      | 60FA 314  | 25    | Dümmlers Chapter 11| e.logston@foo.edu  |
| 1             | 4          | 23.02.21 | Melvin         | Data normalization        | WWH 101   | 75    | Deumlich Chapter 3 | l.melvin@foo.edu   |
| 5             | 2          | 05.05.21 | Logston        | Python and pandas         | 60FA 314  | 92    | Dümmlers Chapter 14| e.logston@foo.edu  |
| 4             | 2          | 04.07.21 | Nevarez        | Spreadsheet aggregate functions | WWH 201 | 65  | Zehnder Page 87    | i.nevarez@foo.edu  |



## 4NF Non-Compliance Explanation

The original dataset is not compliant with the Fourth Normal Form (4NF) due to the presence of multi-valued dependencies. Specifically, a single course can have multiple assignments, and each assignment can be associated with multiple students, grades, and relevant readings. These relationships create multi-valued dependencies, as the assignment topics, grades, and readings are dependent on the combination of student and course, rather than on any single key. Additionally, the same professor might give different assignments with varying due dates and readings to different sections of the same course, introducing further multi-valued dependencies.

## Course Table

| Course ID | Course Name       |
|-----------|-------------------|
| C1        | Database Systems  |
| C2        | Data Analysis     |

## Professor Table

| Professor ID | Professor Name | Professor Email    |
|--------------|----------------|--------------------|
| P1           | Melvin         | l.melvin@foo.edu   |
| P2           | Logston        | e.logston@foo.edu  |

## Classroom Table

| Classroom ID | Classroom Name |
|--------------|----------------|
| R1           | WWH 101        |
| R2           | 60FA 314       |

## Assignment Table

| Assignment ID | Course ID | Professor ID | Classroom ID | Due Date | Assignment Topic        | Relevant Reading      |
|---------------|-----------|--------------|--------------|----------|-------------------------|-----------------------|
| A1            | C1        | P1           | R1           | 23.02.21 | Data normalization      | Deumlich Chapter 3    |
| A2            | C2        | P2           | R2           | 18.11.21 | Single table queries    | Dümmlers Chapter 11   |

## Student Assignment Grade Table

| Student ID | Assignment ID | Grade |
|------------|---------------|-------|
| S1         | A1            | 80    |
| S2         | A2            | 92    |
