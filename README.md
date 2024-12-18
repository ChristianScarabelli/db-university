### 01 Selezionare tutti gli studenti nati nel 1990 (160)

```SQL
SELECT *
FROM students
WHERE YEAR(`date_of_birth`) = 1990;
```

### 02 Selezionare tutti i corsi che valgono più di 10 crediti (479)

```SQL
SELECT * 
FROM `courses`
WHERE `cfu` > 10
```

### 03 Selezionare tutti gli studenti che hanno più di 30 anni (3788)

```SQL
SELECT * 
FROM `students`
WHERE TIMESTAMPDIFF(YEAR, `date_of_birth`, CURDATE()) >= 30;
```
<!-- dove la differenza di data, tra l'anno di nascita e la data corrente è >= a 30 -->

### 04 Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

```SQL
SELECT * 
FROM `courses`
WHERE `period` = 'I semestre' AND `year` = 1;
```

### 05 Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

```SQL
SELECT * 
FROM `exams`
WHERE `date` = '2020-06-20' AND `hour` > '14:00';
```

### 06 Selezionare tutti i corsi di laurea magistrale (38)

```SQL
SELECT * 
FROM `degrees`
WHERE `name`
LIKE '%magistrale%';
```

### 07 Da quanti dipartimenti è composta l'università? (12)

```SQL
SELECT COUNT(*)
FROM `departments`;
```

### 08 Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

```SQL
SELECT *
FROM `teachers`
WHERE `phone` IS NULL;
```

### 09 Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo
### degree_id, inserire un valore casuale)

```SQL
INSERT INTO `students` (`id`, `degree_id`, `name`, `surname`, `date_of_birth`, `fiscal_code`, `enrolment_date`, `registration_number`, `email`) 
VALUES ('1001', '34', 'Christian', 'Scarabelli', '1993-06-24', 'SCRCRS93H24A944G', '2024-09-11', '678900', 'scachmabol@hotmail.it');
```

### 10 Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126

```SQL
UPDATE `teachers` 
SET `office_number` = 126 
WHERE `surname` LIKE 'Rizzo';
```

### 11 Eliminare dalla tabella studenti il record creato precedentemente al punto 9

```SQL
DELETE FROM `exam_student` 
WHERE `student_id` = '1001'; 

DELETE FROM `students` 
WHERE `id` = '1001';
```

<!-- c'è un dato correlato in un'altra tabella: si può eliminare il dato prima nella tabella dipendente e poi in quella principale 
oppure attivare la cancellazione a cascata tra le 2 tabelle  -->