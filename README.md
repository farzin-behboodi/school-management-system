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
| Property / Method | Description |
| :--- | :--- |
| `id` | Unique identifier for each course |
| `name` | Title and name of the course |
| `units` | Number of credits/units for the course |
| `score` | Passing or evaluation score of the course |
| `__eq__(other)` | Compares course equality based on its ID |
| `__str__()` | Returns a formatted string representation of course ID, name, and units |

### Student
| Property / Method | Description |
| :--- | :--- |
| `id` | Unique identification number of the student |
| `name` | First name of the student |
| `family` | Last name of the student |
| `courses` | List of courses enrolled by the student |
| `__eq__(other)` | Compares student equality based on student ID |
| `__str__()` | Returns a string with student ID, name, and family name |
| `print_info_selected_student()` | Displays student profile along with enrolled courses, units, and scores |
| `add_course(selected_course)` | Appends a course to the student course list if not already added |
| `delete_course(course_id)` | Removes a course from the student course list by its ID |
| `add_course_to_select(all_course)` | Prompts for a course ID and adds it to the student courses |
| `delete_course_to_select()` | Prompts for a course ID and removes it from the student courses |
| `set_score()` | Iterates over student courses and sets a new score for each |

### Teacher
| Property / Method | Description |
| :--- | :--- |
| `id` | Unique identification number of the teacher |
| `name` | First name of the teacher |
| `family` | Last name of the teacher |
| `grade` | Academic qualification or degree of the teacher |
| `courses` | List of courses taught by the teacher |
| `__eq__(other)` | Compares teacher equality based on teacher ID |
| `__str__()` | Returns a string with teacher ID, name, family, and grade |
| `print_info_selected_teacher()` | Displays teacher profile details and their assigned courses |
| `add_course_to_select(all_course)` | Prompts for a course ID and adds it to the teacher course list |
| `delete_course_to_select()` | Prompts for a course ID and removes it from the teacher course list |

### Classroom
| Property / Method | Description |
| :--- | :--- |
| `id` | Unique identifier for the classroom |
| `name` | Title or label of the classroom |
| `course` | Course assigned for special or remedial training |
| `teacher` | Instructor assigned to teach the classroom |
| `students` | List of students enrolled in the classroom |
| `__eq__(other)` | Compares classroom equality based on classroom ID |
| `__str__()` | Returns a string summary with ID, name, course, teacher, and student count |
| `print_info_selected_classroom()` | Prints comprehensive classroom details including teacher and enrolled students |
| `change_course(all_course)` | Updates classroom course and filters out invalid teachers or students |
| `change_teacher(all_teacher)` | Reassigns the teacher from instructors qualified for the course |
| `add_student(all_student)` | Enrolls students who scored under 10 in the designated course |
| `remove_student()` | Prompts for a student ID and removes them from the classroom |

### School
| Property / Method | Description |
| :--- | :--- |
| `name` | Name of the school |
| `courses` | Master list of all registered courses |
| `teachers` | Master list of all active teachers |
| `students` | Master list of all enrolled students |
| `classrooms` | Master list of all formed classrooms |
| `selected_student` | Holds the currently selected student in the active session |
| `selected_teacher` | Holds the currently selected teacher in the active session |
| `selected_classroom` | Holds the currently selected classroom in the active session |
| `add_student(student)` | Adds a new student if not already in the school list |
| `add_teacher(teacher)` | Adds a new teacher if not already in the school list |
| `add_course(course)` | Adds a new course if not already in the school list |
| `add_classroom(classroom)` | Adds a new classroom if not already in the school list |
| `print_student()` | Prints the list of all registered students |
| `print_teacher()` | Prints the list of all registered teachers |
| `print_course()` | Prints the list of all registered courses |
| `print_classroom()` | Prints the list of all active classrooms |
| `remove_student(id)` | Deletes a student if they are not enrolled in any active classroom |
| `remove_teacher(id)` | Deletes a teacher if they are not assigned to any classroom |
| `remove_course(id)` | Deletes a course if not utilized by any student, teacher, or classroom |
| `remove_classroom(id)` | Deletes a classroom by its ID |
| `edit_student(student)` | Updates existing student records |
| `edit_teacher(teacher)` | Updates existing teacher records |
| `edit_course(course)` | Updates existing course records |
| `edit_classroom(classroom)` | Updates existing classroom records |
| `load_data()` | Loads school entities and relations from `d3.json` into memory |
| `save_data()` | Serializes and writes all school data back to `d3.json` |