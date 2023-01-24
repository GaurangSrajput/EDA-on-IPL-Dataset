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
