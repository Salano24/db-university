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