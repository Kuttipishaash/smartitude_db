# smartitude_db
Database files related to Smartitude

# Schema documentation

Generated by MySQL Workbench Model Documentation v1.0.0 - Copyright (c) 2015 Hieu Le

## Table: `user`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_user` | INT | PRIMARY, Not null |   |   |
| `email_user` | VARCHAR(255) | Not null |   |   |
| `password_user` | VARCHAR(32) | Not null |   |   |
| `create_time_user` | TIMESTAMP | Not null | `CURRENT_TIMESTAMP` |   |
| `phone_user` | INT | Not null |   |   |
| `type_user` | CHAR(1) | Not null |   |   |
| `name_user` | VARCHAR(45) | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_user` | PRIMARY |   |


## Table: `student`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_stud` | INT | PRIMARY, Not null |   |  **foreign key** to column `id_user` on table `user`. |
| `dept_stud` | TINYINT | Not null |   |  **foreign key** to column `id_dept` on table `department`. |
| `batch_stud` | INT | Not null |   |   |
| `score_stud` | DECIMAL | Not null |   |   |
| `rank_student` | INT |  |   |   |
| `group_stud` | INT | Not null |   |   |
| `semester_stud` | TINYINT | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| id_student_idx | `id_stud` | INDEX |   |
| PRIMARY | `id_stud` | PRIMARY |   |
| id_dept_idx | `dept_stud` | INDEX |   |


## Table: `question`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_qstn` | INT | PRIMARY, Not null |   |   |
| `qstn` | TEXT | Not null |   |   |
| `creator_qstn` | VARCHAR(16) | Not null |   |  **foreign key** to column `id_faculty` on table `faculty`. |
| `category_qstn` | INT | Not null |   |  **foreign key** to column `id_category` on table `category`. |
| `subcat_qstn` | INT | Not null |   |  **foreign key** to column `id_subcat` on table `subcategory`. |
| `approval_stat_qstn` | TINYINT | Not null |   |   |
| `difficulty_qstn` | INT | Not null |   |   |
| `times_attempt_qstn` | INT | Not null | `0` |   |
| `times_solved_qstn` | INT | Not null | `0` |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_qstn` | PRIMARY |   |
| id_creator_idx | `creator_qstn` | INDEX |   |
| category_qstn_idx | `category_qstn` | INDEX |   |
| subcat_qstn_idx | `subcat_qstn` | INDEX |   |


## Table: `faculty`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_faculty` | INT | PRIMARY, Not null |   | Unique identifier field for the faculty<br /><br />**foreign key** to column `id_user` on table `user`. |
| `dept_faculty` | INT | Not null |   | Department to which the faculty belongs to.<br /><br />**foreign key** to column `id_dept` on table `department`. |
| `category_faculty` | INT | Not null |   |  **foreign key** to column `id_category` on table `category`. |
| `subcat_faculty` | JSON | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_faculty` | PRIMARY |   |
| id_dept_idx | `dept_faculty` | INDEX |   |
| category_faculty_idx | `category_faculty` | INDEX |   |


## Table: `department`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_dept` | TINYINT | PRIMARY, Not null |   |   |
| `dept_name` | VARCHAR(45) | Not null |   |   |
| `dept_desc` | TEXT |  |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_dept` | PRIMARY |   |


## Table: `quiz`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_quiz` | INT | PRIMARY, Not null |   |   |
| `name_quiz` | VARCHAR(45) | Not null |   |   |
| `max_solve_time_quiz` | INT | Not null |   |   |
| `targets_quiz` | INT | Not null |   |   |
| `create_time_quiz` | DATETIME | Not null |   |   |
| `expiry_time_quiz` | DATETIME | Not null |   |   |
| `desc_quiz` | TEXT | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_quiz` | PRIMARY |   |


## Table: `admin`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_admin` | INT | PRIMARY, Not null |   | Unique id of the admin |
| `passwd_admin` | VARCHAR(32) | Not null |   |   |
| `create_time_admin` | TIMESTAMP |  |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_admin` | PRIMARY |   |


## Table: `message`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_msg` | INT | PRIMARY, Not null |   |   |
| `title_msg` | VARCHAR(60) | Not null |   |   |
| `desc_msg` | TEXT |  |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_msg` | PRIMARY |   |


## Table: `subcategory`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_subcat` | INT | PRIMARY, Not null |   |   |
| `id_category` | INT | Not null |   |  **foreign key** to column `id_category` on table `category`. |
| `icon_subcat` | TEXT | Not null |   |   |
| `name_subcat` | VARCHAR(45) | Not null |   |   |
| `desc_subcat` | VARCHAR(45) | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_subcat` | PRIMARY |   |
| id_category_idx | `id_category` | INDEX |   |


## Table: `category`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_category` | INT | PRIMARY, Not null |   |   |
| `name_category` | VARCHAR(45) |  |   |   |
| `desc_category` | TEXT |  |   |   |
| `icon_category` | TEXT |  |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_category` | PRIMARY |   |


## Table: `faculty_in_charge`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id_faculty_in_charge` | INT | PRIMARY, Not null |   |  **foreign key** to column `id_faculty` on table `faculty`. |
| `in_charge_subcat` | JSON | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id_faculty_in_charge` | PRIMARY |   |


