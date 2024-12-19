### 1 Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```SQL
SELECT DISTINCT `s`.*
FROM `students` AS `s`
JOIN `courses` ON `s`.`degree_id` = `courses`.`degree_id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';
```
### 2 Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```SQL
SELECT `d`.* 
FROM `departments` AS `d`
JOIN `degrees` 
ON `d`.`id` = `degrees`.`department_id`
WHERE `degrees`.`level` = 'Magistrale' AND `d`.`name` LIKE '%Neuroscienze';
```

### 3 Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```SQL
SELECT `c`.*
FROM `courses` AS `c`
JOIN `course_teacher` ON `c`.`id` = `course_teacher`.`course_id`
JOIN `teachers` AS `t` ON `course_teacher`.`teacher_id` = `t`.`id`
WHERE `t`.`id` = 44;
```

### 4 Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```SQL
SELECT `s`.`id`,`s`.`degree_id`,`s`.`surname`,`s`.`name`, `d`.`name`, `d`.`level`, `dep`.`name`
FROM `students` AS `s`
JOIN `degrees` AS `d`
ON `s`.`degree_id` = `d`.`id`
JOIN `departments` AS `dep`
ON `d`.`department_id` = `dep`.`id`
ORDER BY `s`.`surname`, `s`.`name`;
```

### 5 Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
### 6 Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
### 7 BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.