# SQL-QUERY-NOTES
MY HACKERRANK CHALLENGE NOTES

1) Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.

select distinct(city) from station where (id%2)= 0;

2) Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table

select (count(city) - count(distinct city)) from station;

3) Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

select city,length(city) from station order by length(city) asc, city limit 1;

select city,length(city) from station order by length(city) desc, city limit 1;

4) Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

select distinct(city) frm station where city REGEXP "^[aeiou].*";

5) Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

select distinct(city) from station where city REGEXP '[aeiou]$';

select distinct(city) from station where lower(substr(city,length(city),length(city))) in ('a','e','i','o','u');

syntax-------------------------------
Extract a substring from a string   (start at position 5, extract 3 characters):

SELECT SUBSTR("SQL Tutorial", 5, 3) AS ExtractString;
if lower / upper before substring it denotes cases (lowercase/uppercase)
-------------------------------------

6) Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

select distinct(city) from station where substring(city,1,1) in ('a','e','i','o','u') and substring(city,-1,1) in ('a','e','i','o','u');

7) Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

select distinct(city) from station where not rlike '^[aeiou].*';

8)Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

select distinct(city) from station where lower(substring(city,length(city),1)) in ('a','e','i','o','u');
