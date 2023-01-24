# EDA-on-IPL-Dataset
Exploratory Data Analysis on IPL dataset 
the dataset is all about ipl matches that occured from 2007 to 2019 in which we have 18 columns in the matches table and 21 columns in the Deliveries table.
the matches table has diffrent columns like batsman , bowler, umpire etc.

First step is to import data in the MYSQL Workbench that is an most hectic part beacause Mysql is hell like slow we have to import data through CMD .
mysql -u root -p --local_infile

use ipl

load data local infile 'C:/Users/wINDOWS/Desktop/datset ipl/matches.csv'
 into table matches
     fields terminated by','
     enclosed by '"'
     lines terminated by '\n'
     ignore 1 rows;
     
     
After importing all the tables we can start MYSQL Workbench to Perform EDA-
in the EDA we can create as many insights as we want in this EDA we have asked some of the questions like

1. View Selected Columns
2. show distinct values.
3. Find Season Winner for each Season (Season Winner is the winner ofd the last match of each season.
4. Case (4 run ,6 run Run , Single, O.
5. Data Aggregation Max,Min , Avg (sum Count).
6. How many Extra Runs have been conceded in IPL.
7. On an Average teams won by how many Runs in IPL,
8.How many extra runs were conceded in IPL by SK Warne.


So this the full code performed in EDA of IPL Dataset. results is in attachments--

 select* from ipl.matches;
select*from ipl.deliveries;

#--Shape of Data
# No of Rows

select count(*) as No_of_rows from ipl.matches;
select count(*) as No_of_rows from ipl.deliveries;


# --View Selected Columns 
select season , city, date ,team1 ,team2 from matches;

#__Distinct Values
select distinct season, count(*) from matches group by season;
select distinct city , count(season) from matches group by city;

## Q1-- Find season winner for each season (season winner is the winner of the last match of each season)
select season, winner,max(date) from matches group by season
order by  1 desc;

## Q2-- Find venue of 10 most recently played matches
select venue,max(date) from matches group by venue order by date desc
limit 10;
use ipl;

## Q3 -- Case (4,6 , Single ,0)
select distinct batsman , bowler , case when total_runs =6 then 'Six'
								  when total_runs = 4 then 'Four'
                                  when total_runs = 0 then 'Duck'
                                  when total_runs = 1 then 'Single'
						else
						   'NoRun'
						end as 'Runs in word' from deliveries;
                        
### Q4--Data Aggregation Max,Min, Avg<sum, count

select * from matches ;
select season,winner ,sum(win_by_runs), sum(win_by_wickets) from matches group by season,winner
order by 2 desc;                         
                        
## Q5 -- How many extra runs have been conceded in IPL

select sum(extra_runs) as 'Total Extra Run During IPL' from deliveries;

## Q6-- On an average teams won by how many runs in Ipl

select winner, avg(win_by_runs) as AverageRun from matches group by winner; 

## Q7 -- How many extra runs were conceded in ipl by Sk Warne
select batsman, bowler , sum(extra_runs) from deliveries where bowler='SK Warne'
group by bowler;




If you have any Suggestions Please let me know
Thanks
GAurang
