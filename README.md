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

Represents an academic course in the system.

#### Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `int` | Unique numerical identifier for the course |
| `name` | `str` | Name or title of the course |
| `units` | `int` | Number of course credits or units |
| `score` | `float` | The student's grade or score achieved in this course |

#### Methods

| Method | Parameters | Return Type | Description |
| :--- | :--- | :--- | :--- |
| `__init__` | `id, name, units, score` | `None` | Initializes a new `Course` instance |
| `__eq__` | `other` | `bool` | Compares equality based on course ID |
| `__str__` | `None` | `str` | Returns formatted string representation (`id`, `name`, `units`) |

---

### Student

Represents a student enrolled in the institution.

#### Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `int` | Unique identification number of the student |
| `name` | `str` | First name of the student |
| `family` | `str` | Last name of the student |
| `courses` | `list` | List of `Course` objects enrolled by the student |

#### Methods

| Method | Parameters | Return Type | Description |
| :--- | :--- | :--- | :--- |
| `__init__` | `id, name, family` | `None` | Initializes a new `Student` instance with an empty course list |
| `__eq__` | `other` | `bool` | Compares equality based on student ID |
| `__str__` | `None` | `str` | Returns formatted string representation (`id`, `name`, `family`) |
| `print_info_selected_student` | `None` | `None` | Displays student profile along with enrolled courses, units, and scores |
| `add_course` | `selected_course` | `None` | Appends a course to the student course list if not already added |
| `delete_course` | `course_id` | `None` | Removes an enrolled course from the student course list by its ID |
| `add_course_to_select` | `all_course` | `None` | Prompts for a course ID and adds it to the student courses |
| `delete_course_to_select` | `None` | `None` | Prompts for a course ID and removes it from the student courses |
| `set_score` | `None` | `None` | Prompts and updates the score for each enrolled course |

---

### Teacher

Represents a faculty teacher or instructor in the school.

#### Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `int` | Unique identification number of the teacher |
| `name` | `str` | First name of the teacher |
| `family` | `str` | Last name of the teacher |
| `grade` | `str` | Academic qualification or degree level of the teacher |
| `courses` | `list` | List of `Course` objects taught by the teacher |

#### Methods

| Method | Parameters | Return Type | Description |
| :--- | :--- | :--- | :--- |
| `__init__` | `id, name, family, grade` | `None` | Initializes a new `Teacher` instance |
| `__eq__` | `other` | `bool` | Compares equality based on teacher ID |
| `__str__` | `None` | `str` | Returns formatted string representation (`id`, `name`, `family`, `grade`) |
| `print_info_selected_teacher` | `None` | `None` | Displays teacher profile details and their assigned courses |
| `add_course_to_select` | `all_course` | `None` | Prompts for a course ID and adds it to the teacher course list |
| `delete_course_to_select` | `None` | `None` | Prompts for a course ID and removes it from the teacher course list |

---

### Classroom

Represents a remedial classroom connecting a course, an instructor, and students with low scores.

#### Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `int` | Unique identifier for the classroom |
| `name` | `str` | Title or label of the classroom |
| `course` | `Course` | Course assigned for remedial training |
| `teacher` | `Teacher` | Instructor assigned to teach the classroom |
| `students` | `list` | List of enrolled students in the classroom |

#### Methods

| Method | Parameters | Return Type | Description |
| :--- | :--- | :--- | :--- |
| `__init__` | `id, name` | `None` | Initializes a new `Classroom` instance |
| `__eq__` | `other` | `bool` | Compares equality based on classroom ID |
| `__str__` | `None` | `str` | Returns formatted string summary of the classroom |
| `print_info_selected_classroom` | `None` | `None` | Prints comprehensive classroom details including teacher and enrolled students |
| `change_course` | `all_course` | `None` | Updates classroom course and filters out non-qualifying teachers and students |
| `change_teacher` | `all_teacher` | `None` | Selects and assigns an instructor qualified to teach the course |
| `add_student` | `all_student` | `None` | Enrolls students who scored under 10 in the designated course |
| `remove_student` | `None` | `None` | Prompts for a student ID and removes them from the classroom |

---

### School

Acts as the central controller managing all data entities and persistence.

#### Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `name` | `str` | Name of the school institution |
| `courses` | `list` | Master list of all registered courses |
| `teachers` | `list` | Master list of all registered teachers |
| `students` | `list` | Master list of all enrolled students |
| `classrooms` | `list` | Master list of all formed classrooms |
| `selected_student` | `Student` | Holds the currently selected student in the active menu session |
| `selected_teacher` | `Teacher` | Holds the currently selected teacher in the active menu session |
| `selected_classroom` | `Classroom` | Holds the currently selected classroom in the active menu session |

#### Methods

| Method | Parameters | Return Type | Description |
| :--- | :--- | :--- | :--- |
| `__init__` | `name` | `None` | Initializes a new `School` instance |
| `add_student` | `student` | `None` | Adds a new student if not already registered |
| `add_teacher` | `teacher` | `None` | Adds a new teacher if not already registered |
| `add_course` | `course` | `None` | Adds a new course if not already registered |
| `add_classroom` | `classroom` | `None` | Adds a new classroom if not already registered |
| `print_student` | `None` | `None` | Displays all registered students in the console |
| `print_teacher` | `None` | `None` | Displays all registered teachers in the console |
| `print_course` | `None` | `None` | Displays all registered courses in the console |
| `print_classroom` | `None` | `None` | Displays all active classrooms in the console |
| `remove_student` | `id` | `None` | Removes student by ID if not used in any classroom |
| `remove_teacher` | `id` | `None` | Removes teacher by ID if not assigned to any classroom |
| `remove_course` | `id` | `None` | Removes course by ID if not utilized across the system |
| `remove_classroom` | `id` | `None` | Removes classroom by ID |
| `edit_student` | `student` | `None` | Updates an existing student record |
| `edit_teacher` | `teacher` | `None` | Updates an existing teacher record |
| `edit_course` | `course` | `None` | Updates an existing course record |
| `edit_classroom` | `classroom` | `None` | Updates an existing classroom record |
| `load_data` | `None` | `None` | Deserializes and loads school entities from `d3.json` into memory |
| `save_data` | `None` | `None` | Serializes and writes current school state back to `d3.json` |


## How To Use

When we run this code, the system opens the school program for (sama) with (sc1 = School("sama")) and gets the data from (d3.json) file with (sc1.load_data()).
first for run the code you must write (python school-management-system.py) in the Terminal.
at first the code starts in (level="root") and you see this menu in the Terminal:

```
1.students
2.teachers
3.courses
4.classrooms
5.save
0.exit
choose your option:
```

in this menu you must write a number from 0 to 5 in the Terminal:

* **1.students** :for go to (level="students") and manage the students list you must write (1).
* **2.teachers** :for go to (level="teachers") and manage the teachers list you must write (2).
* **3.courses** :for go to (level="courses") and manage the school courses you must write (3).
* **4.classrooms** :for go to (level="classrooms") and make classes for students with score under 10 you must write (4).
* **5.save** :for run (sc1.save_data()) and save all lists in (d3.json) file you must write (5).
* **0.exit** :for stop the (while True) loop and close the program you must write (0).

when you write (1) in the root menu, the code goes to (level="students") and shows the student menu in the Terminal:

```
1.show student
2.add student
3.edit student
4.delete student
5.select student
0.back
choose your option:
```

in the student menu each number runs one command in the code:

* **1.show student** :for run (sc1.print_student()) and see all students in Terminal you must write (1).
* **2.add student** :for get id, name and family and run (sc1.add_student(Student(id,name,family))) you must write (2).
* **3.edit student** :for change student info with (sc1.edit_student()) you must write (3).
* **4.delete student** :for delete a student with (sc1.remove_student(id)) if they are not in any classroom you must write (4).
* **5.select student** :for select a student by id and go to (level="student_select") you must write (5).
  * inside (student_select) :write (1) for (print_info_selected_student()), write (2) for (add_course_to_select(sc1.courses)) to take a course, write (3) for (delete_course_to_select()), and write (4) for (set_score()) to give score to student courses.
* **0.back** :for go back to the root menu you must write (0).

the other menus in the root menu are just like the student menu so we dont print them again:

* **teachers menu (option 2 in root)** :you can show, add, edit or delete a teacher, or write (5) to go to (level="teacher_select") and give courses to that teacher with (add_course_to_select(sc1.courses)).
* **courses menu (option 3 in root)** :you can add or edit courses, and when you write (4) for delete a course with (sc1.remove_course(id)), first the code checks all lists and if they have that course it shows (this course already use) in the Terminal and doesnt delete it.
* **classrooms menu (option 4 in root)** :when you write (2) for add classroom with (Classroom(id,name)), the code checks (student_course.score < 10) so you only add students with score under 10, and with (5) you go to (level="classroom_select") for change the course, teacher or students.
