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