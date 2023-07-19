create database JD_Daniels1
use JD_daniels1

create or replace TABLE OWNER
(
  OwnerID INTEGER NOT NULL PRIMARY KEY,
  Name VARCHAR(20),
  Surname STRING,
  StreetAdress Varchar(50),
  City String,
  State Char(4),
  Statefull String,
  Zipcode Integer);
  
  Create or Replace Table Pets(
  PetID Varchar(10) Not NULL Primary Key,
  Name Varchar(20),
  Kind String,
  Gender Char(7),
  Age Integer,
  OwnerID integer not null References Owner
  );

  select * from owner;
  select * from Pets;
  
  )
)
select count(DISTINCT OWNERID) FROM OWNER;
SELECT COUNT(DISTINCT PETID) FROM PETS;
--NEED THE NAME OF OWNER & THEIR DOGS NAME ALONG WITH THEIR AGE ----- INNER JOIN
SELECT O. Name AS Owner_Name,p.Name as Pet_name,p.age AS pet_age
from owner o
inner join pets p ON o.OwnerID = p.OwnerID;

---NEED THE NAME OF ALL THE OWNER IRRESPECTIVE WETHER OR NOT THEY ARE HAVING PETS
SELECT O.NAME AS OWNER_NAME,p.Name AS PET_NAME,P.AGE AS PET_AGE
FROM OWNER o
left outer join Pets p ON o.OwnerID = p.OwnerID;

---COUNT OF PETS EACH OWNER HAS
SELECT O.Name AS Owner_name,Count(distinct p.PETID)
From owner o
Inner Join Pets p ON o.OwnerID = p.OwnerID
Group by 1
Order by 2 Desc;

-----RIGHT JOIN
SELECT O.NAME AS OWNER_NAME,P.NAME AS PET_NAME,P.AGE AS PET_AGE
FROM OWNER o
RIGHT JOIN PETS p ON o.OwnerID = p.OwnerID;

----info of all the pets hold by their owner
SELECT DISTINCT KIND FROM PETS;
SELECT KIND,COUNT(*) FROM PETS
GROUP BY 1;

----CROSS JOIN
SELECT O.*,P.*
FROM OWNER O
CROSS JOIN PETS p;
