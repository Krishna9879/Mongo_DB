### **Assignment: Building the "CodingGita Students" Database**

In this article, we will walk through a practical assignment that helps you solidify the concepts you've learned so far. You will be creating a "CodingGita Students" database with two collections: `students` and `courses`. You will also perform basic **CRUD operations** (Create, Read, Update, Delete) to manage the data. By the end of this task, you will have hands-on experience with inserting, querying, and modifying data in MongoDB.

## **Practice Assignments**

### **Task 1: Create a "CodingGita_Students" database**  

#### **1. Create the Database and Collections**

First, let’s create a new database called `CodingGita_Students`. Inside this database, we will create two collections: `students` and `courses`.

**Step 1: Create the database**
```js
use CodingGita_Students // Switch to the CodingGita_Students database. If it doesn't exist, MongoDB will create it automatically.
```

**Step 2: Create the `students` collection**
```js
db.createCollection("students");
```

**Step 3: Create the `courses` collection**
```js
db.createCollection("courses");
```

At this point, you have created an empty database with two collections. Next, let’s move on to adding sample data into these collections.

---

#### **2. Insert Sample Data**

Now, let's insert some sample data into both the `students` and `courses` collections.

**Step 1: Insert sample data into the `students` collection**
```js
db.students.insertMany([
  { 
    "name": "Jenil",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Arjun",
    "rollNumber": 103,
    "department": "Electrical Engineering",
    "year": 3,
    "coursesEnrolled": ["EE101", "EE102"]
  }
]);
```

**Step 2: Insert sample data into the `courses` collection**
```js
db.courses.insertMany([
  { 
    "courseCode": "CS101", 
    "courseName": "Introduction to Programming", 
    "credits": 3, 
    "instructor": "Prof. Sharma" 
  },
  { 
    "courseCode": "CS102", 
    "courseName": "Data Structures", 
    "credits": 3, 
    "instructor": "Prof. Gupta" 
  },
  { 
    "courseCode": "CS103", 
    "courseName": "Algorithms", 
    "credits": 3, 
    "instructor": "Prof. Kapoor" 
  },
  { 
    "courseCode": "EE101", 
    "courseName": "Basic Electrical Engineering", 
    "credits": 4, 
    "instructor": "Prof. Verma" 
  },
  { 
    "courseCode": "EE102", 
    "courseName": "Circuit Theory", 
    "credits": 4, 
    "instructor": "Prof. Yadav" 
  }
]);
```

At this point, you have successfully inserted data into the `students` and `courses` collections.

---

### **Task 2: Perform CRUD operations**  

#### **1. Add a few more students and courses to the database.**


**Step 1: Insert few more sample data into the `students` collection**
```js
db.students.insertMany([
  { 
    "name": "krishna",
    "rollNumber": 104,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "rijans",
    "rollNumber": 105,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },

]);
```
**Step 2: Insert few more sample data into the `courses` collection**
```js
  db.courses.insertMany([
  { 
    "courseCode": "CS104", 
    "courseName": "java Script", 
    "credits": 3, 
    "instructor": "Prof. verma" 
  },
  { 
    "courseCode": "CS105", 
    "courseName": "python", 
    "credits": 3, 
    "instructor": "Prof. patel" 
  },

]);
```

#### **2. Querying Data**

**Step 1: Query students based on department**
If we want to find all students in the **Computer Science** department, we can use the `find` method with a query filter.

```js
db.students.find({ "department": "Computer Science" });
```

This query will return all students who belong to the **Computer Science** department.

**Step 2: Query students based on year**
If we want to find students who are in **year 2**, we can query the `students` collection like this:

```js
db.students.find({ "year": 2 });
```

This will return all students who are in the second year.

**Step 3: Query students by course enrollment**
Let’s say you want to find all students who are enrolled in **CS101**. You can perform the following query:

```js
db.students.find({ "coursesEnrolled": "CS101" });
```

This query will return all students who are enrolled in the **CS101** course.

---

#### **3. Updating Data**

Updating data in MongoDB is easy with the `updateOne` and `updateMany` methods. Let’s go through some examples of how to update data.

**Step 1: Update a student’s courses**
Update the courses for a specific student (e.g., adding a new course).

```js
db.students.updateOne(
  { "name": "rijans" },
  { $push: { "coursesEnrolled": "CS102" } }
);
```
#### **4. Deleting Data**

Deleting data in MongoDB is straightforward. You can use the `deleteOne` or `deleteMany` methods to remove documents.

- Delete a student or course from the database.

**Step 1: Delete a student record**
If we want to delete **Arjun’s** student record from the database, we can do so with the following command:

```js
db.students.deleteOne({ "name": "Arjun" });
```
This will delete the document where the `name` field is **Arjun**.
