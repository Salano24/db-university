GROUP BY:

Contare quanti iscritti ci sono stati ogni anno
- SELECT YEAR(students.enrolment_date) AS anno_iscrizione, COUNT(id) AS numero_iscritti
FROM students
GROUP BY anno_iscrizione;

Contare gli insegnanti che hanno l'ufficio nello stesso edificio
- SELECT teachers.office_address AS ufficio_comune, COUNT(id) AS n_insegnati FROM teachers
GROUP BY ufficio_comune;

Calcolare la media dei voti di ogni appello d'esame
- SELECT exam_id as appello_esame, AVG(exam_student.vote) AS media_voti FROM exam_student GROUP BY appello_esame;


Contare quanti corsi di laurea ci sono per ogni dipartimento
- SELECT degrees.department_id AS dipartimento, COUNT(id)as n_corsi_laurea FROM degrees GROUP BY dipartimento;

-------------------------------------------------------
JOIN:

Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
- SELECT students.* FROM students 
JOIN degrees ON students.degree_id = degrees.id 
WHERE degrees.name = 'Corso di Laurea in Economia';

Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
- SELECT degrees.* FROM degrees 
JOIN departments ON degrees.department_id = departments.id 
WHERE departments.name = 'Dipartimento di Neuroscienze' 
AND degrees.level = 'magistrale';

Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
- SELECT courses.* FROM courses
JOIN course_teacher ON courses.id = course_teacher.course_id 
JOIN teachers ON course_teacher.teacher_id = teachers.id 
WHERE teachers.id = 44;


Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e ilrelativo dipartimento, in ordine alfabetico per cognome e nome
- SELECT students.*, degrees.name as 'nome_corso_di_laurea', departments.name as 'nome_dipartimento' FROM degrees 
JOIN students on degrees.id = students.degree_id 
JOIN departments ON degrees.department_id = departments.id 
ORDER BY students.surname ASC, students.name ASC;

Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
- SELECT degrees.* FROM degrees
JOIN courses ON degree_id = degrees.id
JOIN course_teacher ON courses.id = course_id
JOIN teachers ON teacher_id = teachers.id;

Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
- SELECT DISTINCT teachers.*, departments.name as nome dipartimento FROM course_teacher JOIN teachers ON teachers.id = course_teacher.teacher_id
JOIN courses ON course_teacher.course_id = courses.id
JOIN degrees ON degrees.id = courses.degree_id
JOIN departments ON degrees.department_id = departments.id
WHERE departments.name = 'Dipartimento di Matematica';   

Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
- 