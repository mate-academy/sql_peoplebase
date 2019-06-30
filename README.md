# Peoplebase

Here are eight famous people: 

| Id | First Name | Last Name | Year of Birth | Year of Death |
|----|------------|-----------|---------------|---------------|
| 1  | Marilyn    | Monroe    | 1926          | 1962          |
| 2  | Abraham    | Lincoln   | 1809          | 1865          |
| 3  | Nelson     | Mandela   | 1918          | 2013          |
| 4  | Winston    | Churchill | 1874          | 1965          |
| 5  | Bill       | Gates     | 1955          | –             |
| 6  | Charles    | Darwin    | 1809          | 1882          |
| 7  | Pele       | –         | 1940          | –             |
| 8  | Fidel      | Castro    | 1926          | –             |

1. Using your favorite DB client, design and create a database table called `people` that would store the information presented above (create a database first if you don’t have any existing ones to play with). Don’t bother with creating any keys or indices for now, just create the five columns. Copy and paste the SQL query generated by the client below (it should start with `create table` or something similar; if it is difficult to find the query generated by your client, ask for assistance):

    ```postgresql
	   create table Peoplebase
	(
		id int,
		FirstName text,
		LastName text,
		YearOfBirth int,
		YearOfDeath int
	)
    ```

2. **Manually** create a query or a series of queries that would fill the table with the information above. Put the query/queries below:

    ```postgresql
	INSERT INTO people ("id", "firstname", "lastname", "yearofbirth", "yearofdeath") VALUES
	(1, 'Marilyn', 'Monroe', 1926, 1962),
	(2, 'Abraham', 'Lincoln', 1809, 1865),
	(3, 'Nelson', 'Mandela', 1918, 2013),
	(4, 'Winston', 'Churchill', 1874, 1965),
	(5, 'Bill', 'Gates', 1955, null),
	(6, 'Charles', 'Darwin', 1809, 1882),
	(7, 'Pele', null, 1940, null),
	(8, 'Fidel', 'Castro', 1926, null)
    ```

3. Create a query that would return everything from the table:

    ```postgresql
    select * from people
    ```
    
4. Create a query that would return a single row: the person with the ID of 5.

    ```postgresql
    select * from people where id = 5
    ```

5. Create a query that would return the four people with the following IDs: 1, 3, 7, 8.

    ```postgresql
    select * from people where id in (1, 3, 7, 8)
    ```

6. Create a query that would return all the people except the person with the ID of 4 (`Winston Churchill`).

    ```postgresql
    select * from people where id != 4
    ```

7. Create a query that would select the first names and last names of the people who were born after 1920:

    ```postgresql
    select firstname, lastname from people where yearofbirth > 1920
    ```
    
8. Create a query that would select the IDs of the living people:

    ```postgresql
    select id from people where yearofdeath is null
    ```
    
9. Create a query that would return the years of birth and the years of death of everyone who has died. The columns should be aliased `b` and `d` respectively.

    ```postgresql
    select yearofbirth as b, yearofdeath as d from people where yearofdeath is not null
    ```
    
10. Create a query that would return the list of all years of birth, without repetition:

    ```postgresql
    select distinct yearofbirth from people
    ```

11. Create a query that would select the people with either their first or last name starting with an `M`:

    ```postgresql
    select * from people where firstname like 'M%' or lastname like 'M%'
    ```

12. Create a query that would select the people with both their first and last name starting with an `M`:

    ```postgresql
    select * from people where firstname like 'M%' and lastname like 'M%'
    ```
    
13. Create a query that would select all the people except those whose last name starts with a `C`:

    ```postgresql
    select * from people where lastname NOT like 'C%'
    ```
    
14. Create a query that would select the people whose first name starts with a letter that precedes `M` in the English alphabet:

    ```postgresql
    select * from people where firstname < 'M%'
    ```
    
15. Create a query that would return all the people sorted by their last name alphabetically:

    ```postgresql
    select * from people order by lastname
    ```

16. Create a query that would return the first names of the people sorted in the reverse alphabetical order. The column should be aliased `fn`.

    ```postgresql
    select firstname as fn from people order by firstname desc
    ```

17. Create a query that would return the people sorted by their year of birth in the descending order, and then (if two or more people share the same year of birth) by their last name alphabetically:

    ```postgresql
    select * from people order by yearofbirth desc, lastname
    ```
    
18. Set everyone’s last name to your last name:

    ```postgresql
    update people set lastname = 'Batsenko'
    ``` 
19. Update the first name of everyone who was born before 1900 to your favorite character’s name:

    ```postgresql
    update people set firstname = 'Pavlos' where yearofbirth > 1900
    ```
    
20. Add 1 to both the year of birth and year of death for everyone whose ID is less than 5:

    ```postgresql
    update people set yearofbirth = yearofbirth + 1, yearofdeath = yearofdeath +1 where id < 5
    ```

21. Delete from the table everyone who died before 2000:

    ```postgresql
    delete from people where yearofdeath < 2000
    ```

22. Delete everyone from the table:

    ```postgresql
    delete from people
    ```
