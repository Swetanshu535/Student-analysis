# Student-analysis
This is a small student data base analysis. I have used some queries to solve some questions 

#Q1: Students who are playing chess or bridge or both.
#Q2: Students who are playing chess or bridge.
#Q3. Students who are playing only chess.
#Q4: Students who are playing either chess or bridge but not both.




use student_db;
select * from students;
#Q1: Students who are playing chess or bridge or both.
select c.ID, b.fullname, 'Both' as game
from chess c inner join bridge b on c.ID=b.ID
union 
select c.ID, c.fullname, 'Chess' as game
from chess c left join bridge b on c.ID=b.ID
where b.ID is null
union 
select b.ID, b.fullname, 'Bridge' as game
from bridge b right join chess c on b.ID=c.ID
where c.ID is null;

#Q2: Students who are playing chess or bridge.
select c.ID, c.Fullname, 'Chess' as game
from chess c left join bridge b on c.ID=b.ID
union 
select b.ID,b.fullname, 'bridge' as game
from bridge b right join chess c on c.ID=b.ID;

#Q3. Students who are playing only chess.
select c.ID, c.fullname, 'chess' as game
from chess c left join bridge b on c.ID=b.ID
where b.ID is null;

#Q4: Students who are playing either chess or bridge but not both.
select c.ID, c.fullname, 'Chess' as game
from chess c inner join bridge b on c.ID=b.ID
where b.ID is null
union 
select b.ID, b.fullname, 'Bridge' as game
from bridge b right join chess c on b.ID=c.ID
where c.ID is null;


