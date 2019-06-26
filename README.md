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
    CREATE TABLE people (
    "id" integer,
    "First Name" text,
    "Last Name" text,
    "Year of Birth" integer,
    "Year of Death" integer
    );
    ```

2. **Manually** create a query or a series of queries that would fill the table with the information above. Put the query/queries below:

    ```postgresql
    INSERT INTO people ("id", "First Name", "Last Name", "Year of Birth", "Year of Death")
    VALUES (1, 'Marilyn', 'Monroe', 1926, 1962),
           (2, 'Abraham', 'Lincoln', 1809, 1865),
           (3, 'Nelson', 'Mandela', 1918, 2013),
           (4, 'Winston', 'Churchill', 1874, 1965),
           (5, 'Bill', 'Gates', 1955, null),
           (6, 'Charles', 'Darwin', 1809, 1882),
           (7, 'Pele', '–', 1940, null),
           (8, 'Fidel', 'Castro', 1926, null);
    ```

3. Create a query that would return everything from the table:

    ```postgresql
    SELECT * FROM people;
    ```
    
4. Create a query that would return a single row: the person with the ID of 5.

    ```postgresql
    SELECT *
    FROM people
    WHERE id=5;
    ```

5. Create a query that would return the four people with the following IDs: 1, 3, 7, 8.

    ```postgresql
    SELECT *
    FROM people
    WHERE id IN (1, 3, 7, 8);
    ```

6. Create a query that would return all the people except the person with the ID of 4 (`Winston Churchill`).

    ```postgresql
    SELECT *
    FROM people
    WHERE NOT id=4;
    ```

7. Create a query that would select the first names and last names of the people who were born after 1920:

    ```postgresql
    SELECT "First Name", "Last Name"
    FROM people
    WHERE "Year of Birth">1920;
    ```
    
8. Create a query that would select the IDs of the living people:

    ```postgresql
    SELECT id
    FROM people
    WHERE "Year of Death" IS NULL;
    ```
    
9. Create a query that would return the years of birth and the years of death of everyone who has died. The columns should be aliased `b` and `d` respectively.

    ```postgresql
    SELECT "Year of Birth" b, "Year of Death" d
    FROM people
    WHERE "Year of Death" IS NOT NULL;
    ```
    
10. Create a query that would return the list of all years of birth, without repetition:

    ```postgresql
    SELECT DISTINCT "Year of Birth"
    FROM people;
    ```

11. Create a query that would select the people with either their first or last name starting with an `M`:

    ```postgresql
    SELECT *
    FROM people
    WHERE "First Name" LIKE 'M%' OR "Last Name" LIKE 'M%';
    ```

12. Create a query that would select the people with both their first and last name starting with an `M`:

    ```postgresql
    SELECT *
    FROM people
    WHERE "First Name" LIKE 'M%' AND "Last Name" LIKE 'M%';
    ```
    
13. Create a query that would select all the people except those whose last name starts with a `C`:

    ```postgresql
    SELECT *
    FROM people
    WHERE NOT "Last Name" LIKE 'C%';
    ```
    
14. Create a query that would select the people whose first name starts with a letter that precedes `M` in the English alphabet:

    ```postgresql
    SELECT *
    FROM people
    WHERE "First Name" < 'M';
    ```
    
15. Create a query that would return all the people sorted by their last name alphabetically:

    ```postgresql
    SELECT *
    FROM people
    ORDER BY "Last Name";
    ```

16. Create a query that would return the first names of the people sorted in the reverse alphabetical order. The column should be aliased `fn`.

    ```postgresql
    SELECT "First Name" fn
    FROM people
    ORDER BY "First Name" DESC;
    ```

17. Create a query that would return the people sorted by their year of birth in the descending order, and then (if two or more people share the same year of birth) by their last name alphabetically:

    ```postgresql
    SELECT *
    FROM people
    ORDER BY "Year of Birth" DESC, "Last Name";
    ```
    
18. Set everyone’s last name to your last name:

    ```postgresql
    UPDATE people
    SET "Last Name"='Kondratiuk';
    ```
    
19. Update the first name of everyone who was born before 1900 to your favorite character’s name:

    ```postgresql
    UPDATE people
    SET "First Name"='Hulk'
    WHERE "Year of Birth" < 1900;
    ```
    
20. Add 1 to both the year of birth and year of death for everyone whose ID is less than 5:

    ```postgresql
    UPDATE people
    SET "Year of Birth" = "Year of Birth" + 1,
        "Year of Death" = "Year of Death" + 1
    WHERE id < 5;
    ```

21. Delete from the table everyone who died before 2000:

    ```postgresql
    DELETE FROM people
    WHERE "Year of Death" < 2000;
    ```

22. Delete everyone from the table:

    ```postgresql
    DELETE FROM people;
    ```
    
Don’t forget to create a pull request.
