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
    select location from game where screen_name = "Vesa";
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
    
        -> where country.iso_country = airport.iso_country and  
    
        -> country.name = "Iceland";  

![Exercises 3  Kysymys 1](https://github.com/user-attachments/assets/54397bbd-a7ac-4d5b-b364-6226481f834f)

### Kysymys 2
    select airport.name as "airport name"
        -> from country,airport
        -> where country.iso_country = airport.iso_country and
        -> country.name = "France"
        -> and airport.type like "%large%";
![Exercises 3  Kysymys 2](https://github.com/user-attachments/assets/29325d91-1e4e-4778-a8e5-6a3075d9e0e8)

### Kysymys 3
    select country.name as "country_name" ,airport.name as "airport_name"
        -> from country,airport
        -> where country.iso_country = airport.iso_country and
        -> country.name = "Antarctica";
![Exercises 3  Kysymys 3](https://github.com/user-attachments/assets/53a9c7f5-2a3e-42d0-bfab-ccd4ba4c39f2)

### Kysymys 4
    select airport.elevation_ft
        -> from game,airport
        -> where game.location = airport.ident and
        -> game.screen_name = "Heini"
        -> ;
![Exercises 3  Kysymys 4](https://github.com/user-attachments/assets/195feb0c-b4ba-4540-8c69-2fa0d9eef782)

### Kysymys 5
    select (airport.elevation_ft*0.3048) as elevation_m
        -> from country,airport
        -> where game.location = airport.ident and
        -> game.screen_name = "Heini"
        -> ;
![Exercises 3  Kysymys 5](https://github.com/user-attachments/assets/c62bd9a7-3ca6-45db-94f2-fe54d6fc3d38)

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
        -> where airport.ident =  game.location and
        -> country.iso_country = airport.iso_country and
        -> game.screen_name = "Ilkka"
        -> ;
![Exercises 3  Kysymys 7](https://github.com/user-attachments/assets/fb7e730a-e81f-48ba-b840-32ba22aea91f)

### Kysymys 8
    select goal.name
        -> from game,goal,goal_reached
        -> where game.id = goal_reached.game_id and
        -> goal.id = goal_reached.goal_id and
        -> game.screen_name = "Heini"
        -> ;
![Exercises 3  Kysymys 8](https://github.com/user-attachments/assets/aa209c83-5331-4b61-af85-0cf360ea733e)

### Kysymys 9
    select airport.name
        -> from airport,game,goal,goal_reached
        -> where airport.ident = game.location and
        -> game.id = goal_reached.game_id and
        -> goal.id = goal_reached.goal_id and
        -> game.screen_name = "Ilkka" and
        -> goal.name = "CLOUDS"
        -> ;
![Exercises 3  Kysymys 9](https://github.com/user-attachments/assets/0c1c6b5f-f7aa-4f73-a68e-ad160a17eb59)

### Kysymys 10
    select country.name
        -> from airport,country,game,goal,goal_reached
        -> where country.iso_country = airport.iso_country and
        -> airport.ident = game.location and
        -> game.id = goal_reached.game_id and
        -> goal.id = goal_reached.goal_id and
        -> game.screen_name = "Ilkka" and
        -> goal.name = "CLOUDS"
        -> ;
![Exercises 3  Kysymys 10](https://github.com/user-attachments/assets/11548a6a-3052-4277-b633-b38485accde8)

# Week 4

## Exercises 4: Join

### Kysymys 1 
    select country.name as "country name",airport.name as "airport name"
    -> from country
    -> inner join airport on airport.iso_country = country.iso_country
    -> where country.name = "Finland" and scheduled_service = "yes";
![Exercises 4  Kysymys 1](https://github.com/user-attachments/assets/0b1cdc5b-e113-43ce-a057-06e4d5dd745b)

### Kysymys 2 
    select game.screen_name,airport.name
    -> from game
    -> inner join airport on airport.ident = game.location;
![Exercises 4  Kysymys 2](https://github.com/user-attachments/assets/5dba0d07-f62a-48c8-9a41-a6182a81361e)

### Kysymys 3 
    select game.screen_name,country.name
    -> from game
    -> inner join airport on airport.ident = game.location
    -> inner join country on airport.iso_country = country.iso_country
    -> ;
![Exercises 4  Kysymys 3](https://github.com/user-attachments/assets/13288669-75fe-45b8-896b-ba19d5adc8e5)

### Kysymys 4 
    select airport.name,game.screen_name
    -> from airport
    -> left join  game on game.location = airport.ident
    -> where airport.name like "%Hels%";
![Exercises 4  Kysymys 4](https://github.com/user-attachments/assets/eea01cfc-2941-4bc3-a547-91c50c12bc8a)

### Kysymys 5 
    select goal.name,game.screen_name
    -> from goal
    -> left join goal_reached on goal_reached.goal_id = goal.id
    -> left join game on game.id = goal_reached.game_id;
![Exercises 4  Kysymys 5](https://github.com/user-attachments/assets/2ec85248-829b-4317-9e94-e6541164fa99)

## Exercises 5: Subqueries

### Kysymys 1 
    select name
    -> from country
    -> where iso_country in (
    -> select iso_country
    -> from airport
    -> where name like "Satsuma%");
![Exercises 5  Kysymys 1](https://github.com/user-attachments/assets/dc0a77dc-49bb-4fee-8a0a-9c3bb851c43a)

### Kysymys 2 
    select name
    -> from airport
    -> where iso_country in (
    -> select iso_country
    -> from country
    -> where name = "Monaco");
![Exercises 5  Kysymys 2](https://github.com/user-attachments/assets/b318450d-bc73-43d7-820d-424bf90afa49)

### Kysymys 3 
    select screen_name
    -> from game
    -> where id in (
    -> select game_id
    -> from goal_reached
    -> where goal_id in (
    -> select id
    -> from goal
    -> where name = "CLOUDS" )
    -> );
![Exercises 5  Kysymys 3](https://github.com/user-attachments/assets/db2f70ef-158b-4494-86cc-cdfadf144815)

### Kysymys 4 
    select name
    -> from country
    -> where iso_country not in (
    -> select iso_country from airport) ;
![Exercises 5  Kysymys 4](https://github.com/user-attachments/assets/6a4b0d4c-5ada-479c-b121-b6029c726976)

### Kysymys 5 
    select name
    -> from goal
    -> where id not in (
    -> select goal_id
    -> from goal_reached
    -> where game_id in (
    -> select id
    -> from game
    -> where screen_name = "Heini" )
    -> );
![Exercises 5  Kysymys 5](https://github.com/user-attachments/assets/0a5985bb-09ad-44d8-8ef8-65d08b5b9f22)

# Week 5

## Exercises 6: Aggregate Queries

### Kysymys 1 
    select max(elevation_ft) from airport;
![Exercises 6  Kysymys 1](https://github.com/user-attachments/assets/6bc96cb2-ad83-4551-a34a-f58ee5c39ea4)

### Kysymys 2 
     select continent,count(*)
    -> from country
    -> group by continent;
![Exercises 6  Kysymys 2](https://github.com/user-attachments/assets/1175568c-cc49-4fdf-9468-b73279e6842d)

### Kysymys 3 
    select screen_name,count(*)
    -> from game,goal_reached
    -> where game.id = goal_reached.game_id
    -> group by game.screen_name
    -> ; 
![Exercises 6  Kysymys 3](https://github.com/user-attachments/assets/7aa6d6c0-af7c-490f-a1a7-a6cbf27c43c3)

### Kysymys 4 
    select screen_name
    -> from game
    -> where co2_consumed in (
    -> select min(co2_consumed)
    -> from game
    -> );
![Exercises 6  Kysymys 4](https://github.com/user-attachments/assets/6590b7ac-a0a5-4834-a1f6-a80662aac22e)

### Kysymys 5 
     select country.name,count(*)
    -> from country,airport
    -> where country.iso_country = airport.iso_country
    -> group by country.name order by count(*) desc
    -> limit 50 ;
![Exercises 6  Kysymys 5](https://github.com/user-attachments/assets/9b2981b6-8a90-4df1-ab48-236a14b655c5)

### Kysymys 6 
    select country.name
    -> from country,airport
    -> where country.iso_country = airport.iso_country
    -> group by airport.iso_country
    -> having count(*) >= 1000 ;
![Exercises 6  Kysymys 6](https://github.com/user-attachments/assets/47658ac2-6db9-4b3a-8850-7c3028ab5321)

### Kysymys 7 
    select airport.name
    -> from airport
    -> where elevation_ft in (
    -> select max(elevation_ft)
    -> from airport
    -> );
![Exercises 6  Kysymys 7](https://github.com/user-attachments/assets/ae102f76-8476-458a-9797-ca69b0e00a46)

### Kysymys 8
    select country.name
    -> from country,airport
    -> where country.iso_country = airport.iso_country and
    -> elevation_ft in (
    -> select max(elevation_ft)
    -> from airport
    -> );
![Exercises 6  Kysymys 8](https://github.com/user-attachments/assets/93306833-1a04-48d4-bcf9-a8a9a5e1f939)

### Kysymys 9
     select count(*)
    -> from game,goal_reached
    -> where game.id = goal_reached.game_id
    -> and game.screen_name = "Vesa"
    -> group by game.screen_name
    -> ;
![Exercises 6  Kysymys 9](https://github.com/user-attachments/assets/366724bb-dbba-4024-9ff9-360fa08d6339)

### Kysymys 10
     select airport.name
    -> from airport
    -> where latitude_deg in (
    -> select min(latitude_deg)
    -> from airport
    -> );
![Exercises 6  Kysymys 10](https://github.com/user-attachments/assets/fa38ef39-6c1b-4594-a947-e3291f88a778)

## Exercises 7: Update Queries

### Kysymys 1 
    update game
    -> set location = ( select ident from airport where airport.name = "Nottingham Airport"),co2_consumed = co2_consumed + 500
    -> where screen_name = "Vesa"
    -> ;
![Exercises 7  Kysymys 1](https://github.com/user-attachments/assets/fcf6d635-8f00-4d93-b128-28c8ded89761)

### Kysymys 2
![Exercises 7  Kysymys 2](https://github.com/user-attachments/assets/231b10fa-c4a3-4939-804f-a61b384568b0)

### Kysymys 3 
    delete from goal_reached ;
    select * from goal_reached;
![Exercises 7  Kysymys 3](https://github.com/user-attachments/assets/d8564c19-2a7b-46ac-8c72-5751200c62da)

### Kysymys 4 
    delete from game;
    Query OK, 3 rows affected (0.380 sec)

    MariaDB [flight_game]> select * from game;
    Empty set (0.000 sec)
![Exercises 7  Kysymys 4](https://github.com/user-attachments/assets/ed0aa1da-3071-4cca-9837-4dab1579f288)


