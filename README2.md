// Join

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.`id`,`students`.`name`, `students`.`surname`
FROM `students`
INNER JOIN `degrees`
ON `degrees`.`id` = `students`.`degree_id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze

SELECT * 
FROM `degrees`
INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di neuroscienze';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.


// Group by
1. Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(`enrolment_date`) AS anno_iscrizione, COUNT(*) AS numero_iscritti
FROM `students`
GROUP BY YEAR(`enrolment_date`);

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT `office_address` AS edificio, COUNT(`id`) AS numero_insegnanti
FROM `teachers`
GROUP BY `office_address`;

3. Calcolare la media dei voti di ogni appello d'esame

SELECT `exam_id` as appello_esame_id, AVG(`vote`) as media_voto
FROM `exam_student`
GROUP BY `exam_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT `department_id`, COUNT(`name`) AS corsi_laurea
FROM `degrees`
GROUP BY `department_id`;
