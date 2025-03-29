# # SQL-data-cleaning

This is an educational project on data cleaning and preparation using SQL. The original database in CSV format is located in the file club_member_info.csv. Here, we will explore the steps that need to be applied to obtain a cleansed version of the dataset.
## Data Induction
``` SQL
INSERT INTO club_member_info_cleaned
SELECT * FROM club_member_info;

UPDATE club_member_info_cleaned SET full_name = TRIM(full_name);
 SELECT TRIM(full_name) FROM club_member_info_cleaned cmic ;
UPDATE club_member_info_cleaned SET full_name = UPPER(full_name);
 
 SELECT UPPER(full_name) FROM club_member_info_cleaned cmic ;
 
UPDATE club_member_info_cleaned
SET age = NULL
WHERE age = '';
UPDATE club_member_info_cleaned
SET age = 68
WHERE age > 85;

UPDATE club_member_info_cleaned
SET martial_status = NULL
WHERE martial_status = '';
UPDATE club_member_info_cleaned
SET martial_status = 'divorced'
WHERE martial_status = 'divored';
UPDATE club_member_info_cleaned
SET phone = 'Unknown'
WHERE phone  = '';
UPDATE club_member_info_cleaned
SET job_title = 'Unknown'
WHERE job_title   = '';

UPDATE club_member_info_cleaned 
SET full_address = 'UnKnown'
WHERE full_address LIKE '0%';

UPDATE club_member_info_cleaned cmic
SET membership_date = REPLACE(membership_date, '1,9', '2,0')
WHERE membership_date LIKE '1,9%';
SELECT DISTINCT membership_date 
FROM club_member_info_cleaned;
UPDATE club_member_info_cleaned
SET membership_date = REPLACE(membership_date, '/19', '/20')
WHERE membership_date LIKE '%/19__'; 
```
THE RESULT:
