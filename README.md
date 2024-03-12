# Data Normalization and Entity-Relationship Diagramming

An assignment to normalize the structure of data and establish a set of Entity-Relationship Diagrams for the data.

The contents of this file will be deleted and replaced with the content described in the [instructions](./instructions.md)

## Table containing the original data set

| assignment_id | student_id | due_date | professor      | assignment_topic          | classroom | grade | relevant_reading   | professor_email    |
|---------------|------------|----------|----------------|---------------------------|-----------|-------|--------------------|--------------------|
| 1             | 1          | 23.02.21 | Melvin         | Data normalization        | WWH 101   | 80    | Deumlich Chapter 3 | l.melvin@foo.edu   |
| 2             | 7          | 18.11.21 | Logston        | Single table queries      | 60FA 314  | 25    | Dümmlers Chapter 11| e.logston@foo.edu  |
| 1             | 4          | 23.02.21 | Melvin         | Data normalization        | WWH 101   | 75    | Deumlich Chapter 3 | l.melvin@foo.edu   |
| 5             | 2          | 05.05.21 | Logston        | Python and pandas         | 60FA 314  | 92    | Dümmlers Chapter 14| e.logston@foo.edu  |
| 4             | 2          | 04.07.21 | Nevarez        | Spreadsheet aggregate functions | WWH 201 | 65  | Zehnder Page 87    | i.nevarez@foo.edu  |



## Non-Compliance with Normal Forms

### 2NF Non-Compliance:
The original dataset's compliance with 2NF is contingent upon the identification of a composite key. Assuming a combination of `assignment_id` and `student_id` could serve as such, the dataset does not exhibit clear partial dependencies, which are typical indicators of 2NF violation. However, the lack of an explicit composite key in the given structure means this dataset's alignment with 2NF remains largely theoretical.

### 3NF Non-Compliance:
The dataset likely violates 3NF due to transitive dependencies present. Specifically, attributes such as `professor_email` are dependent on `professor`, which in turn is dependent on `assignment_id`, illustrating a classic transitive dependency scenario. This undermines the requirement that all non-key attributes must be directly dependent on the primary key alone, without any intermediary attributes.

### 4NF Non-Compliance:
The dataset displays multi-valued dependencies, notably between assignments and readings, and between professors and assignments. These dependencies are independent of each other and do not rely on a singular primary key, contravening the core stipulation of 4NF that mandates the absence of non-trivial multi-valued dependencies in the table structure.

## Tables containing the 4NF-compliant version of the data set

### Student Table

| Student_ID | Student Email |
|------------| --------------|
| 1          | ...           |
| 2          | ...           |
| 4          | ...           |
| 7          | ...           |
| ...        | ...           |

### Professor Table

| Professor_ID | Professor_Name | Professor_Email      |
|--------------|----------------|----------------------|
| 1            | Melvin         | l.melvin@foo.edu     |
| 2            | Logston        | e.logston@foo.edu    |
| 3            | Nevarez        | i.nevarez@foo.edu    |
| ...          | ...            | ...                  |

### Course Table



| Course_ID | Course_Name |
|-----------|-------------|
| ...       | ...         |

### Section Table

| Section_ID | Professor_ID | Course_ID | Classroom_ID |
|------------|--------------|-----------|--------------|
| 1          | 1            | 1         | 1            |
| 2          | 1            | 1         | 2            |
| 3          | 2            | 2         | 3            |
| ...        | ...          | ...       | ...          |

### Classroom Table

| Classroom_ID | Classroom_Name |
|--------------|----------------|
| 1            | WWH 101        |
| 2            | 60FA 314       |
| 3            | WWH 201        |
| ...          | ...            |


### Reading Table


| Reading_ID | Title                  | Assignment_ID |
|------------|------------------------|---------------|
| 1          | Deumlich Chapter 3     | 1             |
| 2          | Dümmlers Chapter 11    | 2             |
| 3          | Dümmlers Chapter 14    | 5             |
| 4          | Zehnder Page 87        | 4             |
| ...        | ...                    | ...           |

### Assignment Table

| Assignment_ID | Assignment_Topic                   | Due_Date | Section_ID |
|---------------|------------------------------------|----------|------------|
| 1             | Data normalization                 | 23.02.21 | ...        |
| 2             | Single table queries               | 18.11.21 | ...        |
| 4             | Spreadsheet aggregate functions    | 04.07.21 | ...        |
| 5             | Python and pandas                  | 05.05.21 | ...        |
| ...           | ...                                | ...      | ...        |


### Student Assignment Grading Table

| Student_ID | Assignment_ID | Student_Assignment_Grade |
|------------|---------------|--------------------------|
| 1          | 1             | 80                       |
| 7          | 2             | 25                       |
| 4          | 1             | 75                       |
| 2          | 5             | 92                       |
| 2          | 4             | 65                       |
| ...        | ...           | ...                      |

## The ER diagram you created of your 4NF-compliant version of the data set

## Description of what changes you made and how these changes make the data 4NF-compliant

The changes we made was we took the original table and split it into 8 separate tables that have relationships with each other. Making sure all the tables have non-key fields that must provide a fact about the entity uniquely identified by the primary key. Also making sure that the new tables don’t contain a non-key field is a fact about another non-key field and finally making sure that each record does not contain more than one independent multi-valued fact about an entity. 
We have tables of all the students and professors and their respective emails. 
So, we made a table with the professor IDs that conforms to 4NF also a course table with course ID. 
Then a section table with a section id and what professor is teaching it along with what course is being taught along with what classroom it is being taught it. 
A classroom table with IDs with the classroom’s name. A reading table that includes all the recommended readings and their associated assignments. An assignment table that contains the due date of the assignment and what section it is associated with.

Along with finally a student assignment grading table where the student ID and Assignment ID is used as a composite primary key to match them with their assignment grade.
