### Design DB model for Guvi Zen class ###   
   
THE CODE FOR CREATING THE DATABASE STRUCTURE FOR GUVI ZEN CLASS 

create table student(   
std_id INT PRIMARY KEY ,    
first_name VARCHAR(30),   
last_name varchar(30)   
);   

 create table mentor(   
mtd_id INT PRIMARY KEY ,    
first_name VARCHAR(30),   
last_name varchar(30)   
);   

create table task(   
task_id INT PRIMARY KEY ,    
task_name varchar(50),   
task_description varchar(50),   
std_id int,   
foreign key(std_id) references student(std_id)   
);   

create table class(   
cls_id int primary key ,   
std_id int ,   
mtd_id int ,   
foreign key(std_id ) references student(std_id) ,   
foreign key(mtd_id) references mentor(mtd_id)   
);   

create table attendance(   
att_id int primary key ,   
att_present int ,   
att_absent int,   
std_id int ,   
cls_id int ,   
foreign key(std_id ) references student(std_id) ,   
foreign key(cls_id) references class(cls_id)   
);   

create table dashboard(   
dash_id int primary key ,   
std_id int ,   
mtd_id int ,   
task_id int,   
att_id int,   
foreign key(std_id ) references student(std_id) ,   
foreign key(mtd_id) references mentor(mtd_id),   
foreign key(task_id) references task(task_id),   
foreign key(att_id) references attendance(att_id)   
);   