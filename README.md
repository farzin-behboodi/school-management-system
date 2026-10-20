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

When we run this code, the system opens the school program for (sama) and gets the data from (d3.json) file.
first you write cmd in the Terminal and for run the code you must write (python school-management-system.py) in the Terminal.
in this code we have 5 parts in the root menu and you dont need for install venv or any library in cmd.
you just work with numbers 1 to 5 in Terminal menu, and for back or exit you must write (0) in the Terminal.

for add, edit or delete student, teacher, course and classroom you must select them from the root menu in Terminal.
in the root menu you must write (1) for students, (2) for teachers, (3) for courses and (4) for classrooms.
also inside each menu you must write the id of student, teacher or course for select or edit them in the Terminal.

for save the changes you must write (5) in the root menu and the (save_data) method writes all ids and scores in (d3.json) file.
finally when you open the code again in Terminal, the (load_data) method reads (d3.json) and makes the courses, students, teachers and classrooms.
