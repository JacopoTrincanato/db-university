## QUERY 1 Selezionare tutti gli studenti nati nel 1990 (160)
SELECT name, date_of_birth
FROM students
WHERE YEAR(date_of_birth) = 1990;

## QUERY 2 Selezionare tutti i corsi che valgono più di 10 crediti (479)
SELECT *
FROM courses
WHERE cfu > 10