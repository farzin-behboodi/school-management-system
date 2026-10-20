# School Management System in Python

This project is a simple school management system in python for manage a school with the name (sama) in the Terminal.
the main goal of this project is to keep all school data in one place without need for heavy programs or sql databases.
in this system we have 5 main parts: Course,Student ,Teacher,Classroom and School.

each part in this project keeps the main details for the school.
the (Student) and (Teacher) parts keep the id, name, family, teacher grade and their courses list, and the (Course) part keeps the units and scores.
also the (Classroom) part is for make special classes for students with score under 10 in a course, and it connects one course and one teacher to those students.

all of these parts are inside the main (School) class and it connects all lists together so we dont have wrong or duplicate data in the school.
also this project has a local (d3.json) file next to the python file to keep all courses, students, teachers and classrooms data safe on the computer.