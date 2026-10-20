# School Management System in Python
## introduction
This project is a simple school management system in python for manage a school with the name (sama) in the Terminal.
the main goal of this project is to keep all school data in one place without need for heavy programs or sql databases.
in this system we have 5 main parts: Course,Student ,Teacher,Classroom and School.

each part in this project keeps the main details for the school.
the (Student) and (Teacher) parts keep the id, name, family, teacher grade and their courses list, and the (Course) part keeps the units and scores.
also the (Classroom) part is for make special classes for students with score under 10 in a course, and it connects one course and one teacher to those students.

all of these parts are inside the main (School) class and it connects all lists together so we dont have wrong or duplicate data in the school.
also this project has a local (d3.json) file next to the python file to keep all courses, students, teachers and classrooms data safe on the computer.
## structure
### Course
| Property | Description |
| :--- | :--- |
| `id` | Unique identifier for each course |
| `name` | Title and name of the course |
| `units` | Number of credits/units for the course |
| `score` | Passing or evaluation score of the course |

### Student
| Property | Description |
| :--- | :--- |
| `id` | Unique identification number of the student |
| `name` | First name of the student |
| `family` | Last name of the student |
| `courses` | List of courses enrolled by the student along with their scores |

### Teacher
| Property | Description |
| :--- | :--- |
| `id` | Unique identification number of the teacher |
| `name` | First name of the teacher |
| `family` | Last name of the teacher |
| `grade` | Academic level or degree of the teacher |
| `courses` | List of courses taught by the teacher |

### Classroom
| Property | Description |
| :--- | :--- |
| `id` | Unique identifier for the classroom |
| `name` | Title or label of the classroom |
| `course` | Course assigned for special/remedial training |
| `teacher` | Instructor assigned to the classroom |
| `students` | List of enrolled students who scored under 10 in the course |

### School
| Property | Description |
| :--- | :--- |
| `name` | Name of the school |
| `courses` | Master list of all registered courses |
| `teachers` | Master list of all active teachers |
| `students` | Master list of all enrolled students |
| `classrooms` | Master list of all formed classrooms |