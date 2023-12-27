1. Используя команду cat в терминале операционной системы Linux, создать
два файла Домашние животные (заполнив файл собаками, кошками,
хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и
ослы), а затем объединить их. Просмотреть содержимое созданного файла.
Переименовать файл, дав ему новое имя (Друзья человека).
![1](https://github.com/EvgeniiK89/FinalWork.Developer/assets/90926703/98db6ed3-c75f-4f7b-b37b-ca857a67cae8)

2. Создать директорию, переместить файл туда
![2](https://github.com/EvgeniiK89/FinalWork.Developer/assets/90926703/76013537-4c5c-4acb-8c86-c7823494c52b)

3. Подключить дополнительный репозиторий MySQL. Установить любой пакет
из этого репозитория.
![3](https://github.com/EvgeniiK89/FinalWork.Developer/assets/90926703/0dcc1cba-0837-4069-9d1b-0d78f417c0c5)

4. Установить и удалить deb-пакет с помощью dpkg.
![4](https://github.com/EvgeniiK89/FinalWork.Developer/assets/90926703/29353c2d-1568-4c4d-b9c7-b9d087932e5c)

5. Выложить историю команд в терминале ubuntu
{
1 TASK:
   $ mkdir FinalWork
   $ cd FinalWork/
   $ cat > pets.txt
dogs
cat
hamsters
   $ cat > pack_animals.txt
horses
camels
donkeys
   $ cat pets.txt pack_animals.txt > all_animals
   $ mv all_animals human_friends

2 TASK: 
   $ mkdir ZOO_Folder
   $ mv human_friends ZOO_Folder/

3 TASK: 
   # apt update
   # apt upgrade
   # apt-get install mysql-server
   # mysqld --version

4 TASK: 
   # dpkg -i mysql-apt-config_0.8.12-1_all.deb
   # dpkg -r mysql-apt-config
   }

6. Нарисовать диаграмму, в которой есть класс родительский класс, домашние
животные и вьючные животные, в составы которых в случае домашних
животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные
войдут: Лошади, верблюды и ослы).
![6](https://github.com/EvgeniiK89/FinalWork.Developer/assets/90926703/51e46ff2-9cc4-4a78-afb2-5a0f6cd755e4)

7. В подключенном MySQL репозитории создать базу данных “Друзья
человека”.
8. Создать таблицы с иерархией из диаграммы в БД
![8](https://github.com/EvgeniiK89/FinalWork.Developer/assets/90926703/18d6879b-dcb9-4f76-a6d2-dd1973df6e28)

9. Заполнить низкоуровневые таблицы именами(животных), командами
которые они выполняют и датами рождения
![9](https://github.com/EvgeniiK89/FinalWork.Developer/assets/90926703/96a1e089-e0b8-4cc6-82b0-446c445cd599)

10. Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой
питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу.
![10](https://github.com/EvgeniiK89/FinalWork.Developer/assets/90926703/a2a0356b-c82e-4e6a-b203-7dcce2c1f931)
_____________________________________________________________________________________________________________
Скрипты команд в WorkBench

CREATE DATABASE human_friends;
USE human_friends;
CREATE TABLE animals
(
	Id INT AUTO_INCREMENT PRIMARY KEY, 
	type_animal VARCHAR(20)
);

INSERT INTO animals (type_animal)
VALUES ('Pets'),
('Pack_animal');  

CREATE TABLE pets
(
	  Id INT AUTO_INCREMENT PRIMARY KEY,
    kind_animal VARCHAR (20),
    class_id INT,
    FOREIGN KEY (class_id) REFERENCES animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO pets (kind_animal, Class_id)
VALUES ('Cat', 1),
('Dog', 1),  
('Hamster', 1); 

CREATE TABLE pack_animals
(
	  Id INT AUTO_INCREMENT PRIMARY KEY,
    kind_animal VARCHAR (20),
    class_id INT,
    FOREIGN KEY (class_id) REFERENCES animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO pack_animals (kind_animal, class_id)
VALUES ('Horse', 2),
('Camel', 2),  
('Donkey', 2); 

CREATE TABLE cats 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthyear INT,
    Command VARCHAR(50)
);

INSERT INTO cats (Name, Birthyear, Command)
VALUES ('Murzik', 2015, 'Say meow'),
('Barsik', 2017, 'Jump'),  
('Kotya', 2016, 'Lie down'); 

CREATE TABLE dogs 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthyear INT,
    Command VARCHAR(50)
);

INSERT INTO dogs (Name, Birthyear, Command)
VALUES ('Sharik', 2019, 'Bring the stick'),
('Bobik', 2022, 'Sit'),  
('Tuzik', 2013, 'Voice');

CREATE TABLE hamsters 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthyear INT,
    Command VARCHAR(50)
);

INSERT INTO hamsters (Name, Birthyear, Command)
VALUES ('Lil', 2020, 'Eat'),
('Brauni', 2023, 'Sleep'),  
('Fat Joe', 2022, 'Do nothing');

CREATE TABLE horses 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthyear INT,
    Command VARCHAR(50)
);

INSERT INTO horses (Name, Birthyear, Command)
VALUES ('Flash', 2009, 'Run fast'),
('Speedy', 2014, 'Slow down'),  
('Wind', 2019, 'Stop');

CREATE TABLE donkeys 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthyear INT,
    Command VARCHAR(50)
);

INSERT INTO donkeys (Name, Birthyear, Command)
VALUES ('Dummie', 2005, 'Stop'),
('Bogdan', 2012, 'Go'),  
('The Nice', 2015, 'Return');

CREATE TABLE camels 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthyear INT,
    Command VARCHAR(50)
);

INSERT INTO camels (Name, Birthyear, Command)
VALUES ('Bruce', 2016, 'Run'),
('Wild', 2017, "Left"),  
('Top-Top', 2018, "Right");

SET SQL_SAFE_UPDATES = 0;
DELETE FROM camels;

SELECT Name, Birthyear, Command FROM horses
UNION SELECT  Name, Birthyear, Command FROM donkeys;

