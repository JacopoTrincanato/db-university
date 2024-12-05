TODO:

# Group by:

## Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(*) AS 'enrolment_numb', YEAR(enrolment_date) AS enrolment_per_year
FROM students
GROUP BY enrolment_per_year

## Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(*) AS 'offices_numb',  office_address
FROM teachers
GROUP BY office_address 

## Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(vote) AS 'average_mark',  exam_id
FROM exam_student
GROUP BY exam_id 

## Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT('id') AS 'total_courses',  department_id
FROM degrees
GROUP BY department_id 

# Joins:

## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT students.id AS student_id, 
students.name AS student_name, 
degrees.id AS degree_id, 
degrees.name AS degree_name
FROM students
JOIN degrees
ON students.degree_id = degrees.id
WHERE degrees.name = 'Corso di Laurea in Economia'

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT degrees.id AS degree_id, 
degrees.name AS degree_name,
departments.name as department_name
FROM degrees
JOIN departments
ON degrees.department_id = departments.id
WHERE degrees.level = 'magistrale'
AND departments.name = 'Dipartimento di Neuroscienze'

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT DISTINCT teachers.name, teachers.surname, course_id, courses.name
FROM teachers
JOIN course_teacher ON course_teacher.teacher_id = teachers.id
JOIN courses ON course_teacher.course_id = courses.id
WHERE teachers.id = 44

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT students.name, students.surname, department_id, degree_id, degrees.name
FROM students
JOIN degrees ON students.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
ORDER BY students.surname 

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT *
FROM degrees
JOIN courses ON courses.degree_id = degrees.id
JOIN course_teacher ON course_teacher.course_id = courses.id
JOIN teachers ON course_teacher.teacher_id = teachers.id

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
SELECT DISTINCT teachers.*
FROM teachers
JOIN course_teacher ON teachers.id = course_teacher.teacher_id
JOIN courses ON course_teacher.course_id = courses.id
JOIN degrees ON courses.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
WHERE departments.name = 'Dipartimento di Matematica';

## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.