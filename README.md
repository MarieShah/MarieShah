# CP Solver OUA Sports Scheduling 🏀

## Description

This CP model was implements to solve the sports scheduling problem of minimizng the total travel time of the Ontario University Athletics Association (OUA) men’s basketball league in a round robin tournament.

The CP program was formulated as follows: 

Constant Sets:
- T = {1, 2, …, t} , set of Teams
- C = {1, 2, .., c}: Set of conferences.
- W = {1, 2, …, w}: Set of weeks in the regular season, accounts for December break.
- G = {1, 2, …, g}: Set of games each team must play.

Parameters:
- di,j : distance between team i and team j
- ci,j : 1 if team i and team j are in the same conference

Decision Variable:
- xijk : interval variable that represents a game between team i and j at k, indicating home(k=0) or away (k=1) for team i

Domain:  xijk is present if a match is scheduled

Objective Function: min   Dmax, where Dmax is the maximum total travel distance among all teams.

Constraints implemented: 
- Round Robin Constraint: Each pair of teams must play twice (home and away) if they are in the same conference
- One inter-conference game: Each team plays exactly one home and one away game with a team from a different conference
- Max travel distance: The maximum total travel distance, Dmax  must be greater or equal to the total distance travelled by the rest of teams.
- Total number of games: Each team plays exactly G - 1 matches
- Equal number of home and away games: Teams must have the same number of home and away games
- Same conference constraint: Teams in the same conference must play two games, one home and one away
- Max consecutive away games: Each team plays at most two away games in a row

## Getting Started
Program can be run on google colab for up to instances of 18 teams. 

Note: It does take longer as the instance size grows.

### 1.0 Dependencies
The program uses CPlex's CP solver integrated wiht python. Intalling the following is required:
-  !pip install cplex
-  !pip install docplex
- !pip install ortools


### 2.0 Installing
- Open the program in google cplab and mount your google dirve to access the instance files
- from google.colab import drive
drive.mount('/content/drive') 
Import the following libraries:
- from docplex.cp.model import CpoModel
- import cplex
- import pandas as pd
- import numpy as np
- from ortools.sat.python import cp_model
- import time
  
### 3.0 Importing Data
Enter your filepath at : 
  - datafile = "your file path"

Your file will be read and the followign extracted:
- Team = Teams {1,2..,18}
- T =  Number of teams
- W = Number of weeks
- c = Conferences
- Conferences = Number of conferences

- Returns the following:  Teams, T, W, c, Conferences, d

### 4.0 Reading Data
- Start the timer
- Call the read_file function to load data
- Convert the distances to a NumPy array for easy computing
- Prints the distances

### 5.0 Executing the program
- Program run the program once steps 1.0 to 4.0 are compelted see step 6.0 for support

## Help
- You may run into the issue of the code taking long to run for larger instances, this is due to the google colab being limtied to the CPlex public version
- Running the program using CPlex academic can solve this issue 

## Authors

Marie Shah, Alex Harb, Natalia Luna Souza, Nicole Le

