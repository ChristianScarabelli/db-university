### 1 Contare quanti iscritti ci sono stati ogni anno

```SQL
SELECT COUNT(*) AS `enrolment_count_each_year`, YEAR(`enrolment_date`) AS `enrolment_year`
FROM `students`
GROUP BY YEAR(enrolment_date);
```

### 2 Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```SQL
SELECT `office_address`, COUNT(*) AS `office_count` 
FROM `teachers` 
GROUP BY `office_address`;
```

### 3 Calcolare la media dei voti di ogni appello d'esame

```SQL
SELECT `exam_id`, AVG(`vote`) AS `average_vote`
FROM exam_student
GROUP BY `exam_id`;
```
### 4 Contare quanti corsi di laurea ci sono per ogni dipartimento

```SQL
SELECT `department_id`, COUNT(*) AS `course_count` 
FROM degrees
GROUP BY `department_id`;
```