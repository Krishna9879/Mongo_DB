### **More Practice Tasks**

### **Task 1: Add multiple students**  

- Insert at least 5 students into the students collection with unique roll numbers, names, departments, years, and subjects enrolled.
**Step 1: Insert sample data into the `students` collection**

```js
db.students.insertMany([
  { 
    "name": "Jenil",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "MongoDB"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS"]
  },
  { 
    "name": "krishna",
    "rollNumber": 103,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS","javaScript"]
  },
  { 
    "name": "aditya",
    "rollNumber": 104,
    "department": "Computer Science",
    "year": 2,
    "subjectsEnrolled": ["React", "NodeJS","Figma"]
  },
  { 
    "name": "Arjun",
    "rollNumber": 105,
    "department": "Electrical Engineering",
    "year": 3,
    "subjectsEnrolled": ["Circuit Theory", "Electrical Machines"]
  }
]);
```
---

### **Task 2: Add multiple subjects**  

- Insert 4 subjects into the subjects collection, each with 3 to 5 topics.

**Step 1: Insert sample data into the `students` collection**

```js
db.subjects.insertMany([
  { 
    "subjectName": "React",
    "topics": [
      "JSX", 
      "Components", 
      "State", 
      "Props", 
      "Hooks"
    ]
  },
  { 
    "subjectName": "NodeJS", 
    "topics": [
      "Modules", 
      "Express", 
      "File System", 
      "Asynchronous Programming"
    ]
  },
  { 
    "subjectName": "MongoDB", 
    "topics": [
      "Database Design", 
      "CRUD Operations", 
      "Aggregation", 
      "Indexes"
    ]
  },
  { 
    "subjectName": "JavaScript", 
    "topics": [
      "String", 
      "Variables", 
      "operators", 
      "Functions"
    ]
  }
]);
```
---

### **Task 3: Query students based on subject enrollment**  

- Query the `students` collection to find all students who are enrolled in NodeJS.

**Step 1: Query students by subject enrollment**
To find all students enrolled in the NodeJS subject:

```js
db.students.find({ "subjectsEnrolled": "NodeJS" });
```
---

### **Task 4: Add a new topic to a subject**  

**Let’s say we want to add a new topic, "API", to the NodeJS subject:**
- Add a new topic to the NodeJS subject.

```js
db.subjects.updateOne(
  { "subjectName": "NodeJS" },
  { $push: { "topics": "API" } }
);
```
---

### **Task 5: Query subjects with multiple topics**  

**Query the subjects collection to find subjects that contain at least 4 topics.**

- To find the subject which contains the topic "Hooks":

```js
db.subjects.find({ topics: { $size: { $gte: 4 } } });

```
---

### **Task 6: Update student enrollment**  

**We will now update data using MongoDB's updateOne and updateMany methods.**

- Add the subject "React Native" to Jenil's subjects.

```js
db.students.updateOne(
  { "name": "Jenil" },
  { $push: { "subjectsEnrolled": "React Native" } }
);
```
---

### **Task 7: Query all students**  

- **Query all students in the database and print out their names and enrolled subjects.**

```js
db.students.find({}, { name: 1, subjectsEnrolled: 1, _id: 0 });
```
---

### **Task 8: Update multiple students' year**  

- **Update the year for all students in the Computer Science department to year 3.**

```js
db.students.updateMany(
  { department: "Computer Science" },
  { $set: { year: 3 } }
);
```
---
### **Task 9: Add new topics to multiple subjects**  

- **Add new topics to React, NodeJS, and MongoDB subjects. Ensure each subject gets at least one new topic.**

```js
db.subjects.updateOne(
  { name: "React" },
  { $push: { topics: "Context API" } }
);

db.subjects.updateOne(
  { name: "NodeJS" },
  { $push: { topics: "Event Loop" } }
);

db.subjects.updateOne(
  { name: "MongoDB" },
  { $push: { topics: "Transactions" } }
);
```
---

### **Task 10: Remove a topic from a subject**  

- **Remove the topic "Express" from the NodeJS subject**

```js
db.subjects.updateOne(
  { name: "NodeJS" },
  { $pull: { topics: "Express" } }
);

```
### **Task 11: Query all students in a specific year**  

- **Query and return all students in year 2 or year 3.**

```js
db.students.find({ year: { $in: [2, 3] } });

```
---
### **Task 12: Delete a student by roll number**  

- **Delete a student from the database using their roll number.**

```js
db.students.deleteOne({ rollNumber: 105 });
```
---
### **Task 13: Delete all students from a department**  

- **Delete all students who belong to the Electrical Engineering department.**

```js
db.students.deleteMany({ department: "Electrical Engineering" });
```
---
### **Task 14: Retrieve all topics for a subject**  

- **Query the MongoDB subject and retrieve all topics listed for it.**

```js
  db.subjects.find(
  { name: "MongoDB" },
  { topics: 1, _id: 0 }
);
```
---
### **Task 15: Count the number of subjects in which a student is enrolled**  

- **Write a query that returns the number of subjects each student is enrolled in.**

```js
db.students.aggregate([
  {
    $project: {
      name: 1,
      subjectCount: { $size: "$subjectsEnrolled" }
    }
  }
]);
```
