# Week 3

## Exercises 2: Single Table Queries

### Kysymys 1  
    select * from goal;
![Exercises 2  Kysymys 1](https://github.com/user-attachments/assets/7a11caa7-b410-493a-9736-58006528ae8c)

### Kysymys 2
    select name,type from airport where iso_country = "FI";
![Exercises 2  Kysymys 2](https://github.com/user-attachments/assets/6eb9ba4a-1dec-49fd-9bbd-29b97b4f044c)

### Kysymys 3
    select name from airport where iso_country = "FI" order by name asc;
![Exercises 2  Kysymys 3](https://github.com/user-attachments/assets/cc50430e-e38e-441a-a1e2-5dbd589c05b2)

### Kysymys 4
    select name,type from airport where iso_country = "FI" order by type asc , name asc;
![Exercises 2  Kysymys 4](https://github.com/user-attachments/assets/e9a0fd84-2089-43f9-b599-dbc49f9e4c3c)

### Kysymys 5
    select name from country where name like  "F%";
![Exercises 2  Kysymys 5](https://github.com/user-attachments/assets/d872edd6-53f9-4539-8b62-93d875388e20)

### Kysymys 6
    select name from country where name like  "%F%";
![Exercises 2  Kysymys 6](https://github.com/user-attachments/assets/546ac9dd-20fb-4302-842d-67d81e211946)

### Kysymys 7
    select location from game where screen_name = "Vesa" ;
![Exercises 2  Kysymys 7](https://github.com/user-attachments/assets/afec06c3-1582-4ace-8d8f-c1d5b57bb617)

### Kysymys 8
    select co2_consumed from game where screen_name = "Ilkka";
![Exercises 2  Kysymys 8](https://github.com/user-attachments/assets/6f058e9f-7db1-40d5-bf77-d152d3d33a38)

### Kysymys 9
    select DISTINCT co2_budget from game where co2_budget = "10000";
![Exercises 2  Kysymys 9](https://github.com/user-attachments/assets/18be5fe1-de51-48e5-87d9-d6b3d73c2e9f)

### Kysymys 10
    select screen_name , co2_budget, co2_consumed , (co2_budget - co2_consumed) as co2_left from game where screen_name = "Ilkka";
![Exercises 2  Kysymys 10](https://github.com/user-attachments/assets/bbf489e0-55b3-45b7-bbd3-6c4a00dabca5)

## Exercises 3: Multiple Table Queries

### Kysymys 1
    select country.name as "country name" ,airport.name as "airport name"  

        -> from country,airport  
    
        ->  where country.iso_country = airport.iso_country and  
    
    ->  country.name = "Iceland";  

![Exercises 3  Kysymys 1](https://github.com/user-attachments/assets/54397bbd-a7ac-4d5b-b364-6226481f834f)

### Kysymys 2
    select airport.name as "airport name"
        -> from country,airport
        ->  where country.iso_country = airport.iso_country and
        ->  country.name = "France"
        -> and airport.type like "%large%"
![Exercises 3  Kysymys 2](https://github.com/user-attachments/assets/29325d91-1e4e-4778-a8e5-6a3075d9e0e8)

### Kysymys 3
    select country.name as "country_name" ,airport.name as "airport_name"
        -> from country,airport
        ->  where country.iso_country = airport.iso_country and
    ->  country.name = "Antarctica";
![Exercises 3  Kysymys 3](https://github.com/user-attachments/assets/53a9c7f5-2a3e-42d0-bfab-ccd4ba4c39f2)

### Kysymys 4
    select airport.elevation_ft
        -> from game,airport
        -> where game.location = airport.ident and
        -> game.screen_name = "Heini"
        -> ;
![Exercises 3  Kysymys 4](https://github.com/user-attachments/assets/195feb0c-b4ba-4540-8c69-2fa0d9eef782)

### Kysymys 5
    select (airport.elevation_ft/3) as elevation_m
        -> from country,airport
        ->  where country.iso_country = airport.iso_country and
    ->  country.name = "Iceland";
![Exercises 3  Kysymys 5](https://github.com/user-attachments/assets/e773f868-e9d7-4b10-961c-cef66b49889f)

### Kysymys 6
    select name
        -> from airport,game
        -> where airport.ident =  game.location and
        -> game.screen_name = "Ilkka"
        -> ;
![Exercises 3  Kysymys 6](https://github.com/user-attachments/assets/d470f8a4-fb9d-4984-aa46-b5ccd182ec12)

### Kysymys 7
    select country.name
        -> from airport,game,country
        ->  where airport.ident =  game.location and
        -> country.iso_country = airport.iso_country and
        ->  game.screen_name = "Ilkka"
        -> ;
![Exercises 3  Kysymys 7](https://github.com/user-attachments/assets/fb7e730a-e81f-48ba-b840-32ba22aea91f)

### Kysymys 8
    select goal.name
        -> from game,goal,goal_reached
        ->  where game.id = goal_reached.game_id and
        -> goal.id = goal_reached.goal_id and
        -> game.screen_name = "Heini"
        -> ;
![Exercises 3  Kysymys 8](https://github.com/user-attachments/assets/aa209c83-5331-4b61-af85-0cf360ea733e)

### Kysymys 9
    select airport.name
        ->  from airport,game,goal,goal_reached
        ->  where airport.ident = game.location and
        -> game.id = goal_reached.game_id and
        -> goal.id = goal_reached.goal_id and
        -> game.screen_name = "Ilkka" and
        -> goal.name = "CLOUDS"
        -> ;
![Exercises 3  Kysymys 9](https://github.com/user-attachments/assets/0c1c6b5f-f7aa-4f73-a68e-ad160a17eb59)

### Kysymys 10
    select country.name
        -> from airport,country,game,goal,goal_reached
        ->  where country.iso_country = airport.iso_country and
        ->  airport.ident = game.location and
        -> game.id = goal_reached.game_id and
        -> goal.id = goal_reached.goal_id and
        -> game.screen_name = "Ilkka" and
        -> goal.name = "CLOUDS"
        -> ;
![Exercises 3  Kysymys 10](https://github.com/user-attachments/assets/11548a6a-3052-4277-b633-b38485accde8)
