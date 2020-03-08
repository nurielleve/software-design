# Assignment 1
Maximum number of words for this document: 2500


## Introduction									
Author(s): Nuriel Leve, Amanda Patterson, Dominic Smorra, Lucy Lawrence 

For this project we’re targeting users who are interested in playing Fantasy Soccer within the Premier League. By interacting with the command-line interface, this user will be able to register in an open league or create a new one. Once the league is closed, in the 24 hour period after, there will be a draft. Users will form a team, or teams, of players composed of one goalkeeper, four defenders, four midfielders, and two attackers. They may choose players from any team within the Premier league; however, if there are multiple teams, a player may only be on one team at a time. The order teams may draft players in is set randomly, or can be chosen explicitly by the league manager. After the draft, they can then schedule games between members of that league. It is only the ‘league manager,’ or user who created the league, who is able to close the league and schedule the games between teams. This user will also have the option to opt for a randomized schedule, which would pair teams at random. Matches will be ‘played’ each Sunday according to the created schedule. A team will win the match if their total score is higher than their opponents. A score is tallied by adding up the points each player on their team has earned. In our system, player statistics will be provided manually by the league manager. Players are either on a team or in the pool of free players, and for 24 hours after the last game is played on Sunday, users can swap their players for players in the pool to improve their team. They can also ask for trades with other teams. When a team receives a trade request they can accept, deny, or send an alternative request. Users will also be able to see the current ranking of the teams in their league. A user wins the league by scoring the most points at the end of the scheduled matchups. The point system for the users depends on the score gained by their team(s), the higher the points for the user the higher they rank in the league rankings. Points may not be deducted, but only gained through winning matchups - the scoring system from the matchups depends on rubriks such as goals scored, penalties gained etc.
 
We got inspiration from https://fantasy.premierleague.com/. We also looked at https://en.wikipedia.org/wiki/Fantasy_football_(association) for background knowledge.

## Features
Author(s): Nuriel Leve, Amanda Patterson, Dominic Smorra, Lucy Lawrence 


### Functional features

When defining the functional requirements we attempted to be as complete as possible. We went through the two types of users, league managers and team managers, and then thought of all possible actions each type of user should be able to complete. We then brainstormed the other aspects the system must have in order for those actions to be completed. We have listed the features in what we believe is the order of importance / how critical they are to the system.

| ID  | Short name  | Description  |
|---|---|---|
| F1  | League Creation and Set Up | The first user to enter the system will create the League and become the league manager. The system will guide this user through setting up the league. This is highly important because then other users will be able to join the league once it is set up. The league manager will have special permission level to issue certain commands. The league manager may be asked to verify it is them by inputting a password or id. | 
| F2  | Team creation and joining League | Users may create teams, becoming Team managers, and join the league once it has been set up and is open. This is a critical functionality of our system. Users must be able to have their own teams in order to participate in Fantasy Soccer. Only the league manager has control over whether the league is open or closed to new teams. | 
| F3 | Drafting Procedures | The league manager may set the draft order that teams may draft players in. Once the league is closed by the league manager the drafting begins. Team managers must be able to select players and add them to their teams in the order specified by the league manager.| 
| F4 | Scheduling Matches | The league manager will issue a command for the schedule to be created. This will create the schedule for which team is up against which team for each week. Once that is done the matchups will be created between the teams. 
| F5 | Entering Statistics and Earning Points | The league manager will enter how many fantasy points each soccer player has earned over the course of the week. This will be used to calculate each teams points and which team won their matchup that week. This will be added to the teams record. Players stop earning points on Sunday from the previous week and that is when the league manager should input stats. 
| F6  | Team Commands  | The team manager of a team can add and remove players to their team by issuing command-line commands following this syntax: `command-name [target-objects]*`. The available `command-names` are the following: <br/> - trade: ... <br/> - draft: ... <br/> - drop: ... |
| F7  | Team Ranking Viewing Interface  | It is highly important that everyone be able to see the statistics of the teams and rankings. Team Managers should be able to know their schedule for the rest of the season, the ranking of the teams in the league, and stats about their own team. The system should provide an interface where they can see this. |
| F8  | Player Viewing Interface  | It is highly important that everyone be able to see the statistics of the players. This is important in making drafting and trading decisions. Team Managers should be able to know what players are available, what position these players are and their record in the past.|
| F7  | Player Changes | The system should not allow any changes to teams except for the 24 hour window after the last game on Sunday. |
| F8  | Team Management  | The system will only keep track of players and their positions, only allowing teams of one goalkeeper, four defenders, four midfielders, and two attackers, and ensuring players are only on one team at a time.  |
| F9  | Player Trades | When a trade is sent from team to another in the form of the command: <br/> trade [sending team] [receiving team] [sending player] [receiving player] <br/> The receiving team may accept, y, deny, n, or deny and send an alternative trade in the same form. |


### Quality requirements
Author(s): Nuriel Leve, Amanda Patterson, Dominic Smorra, Lucy Lawrence 

To define the quality requirements we brainstormed the aspects of the system which make it more reliable, more secure and more useable. We first went through the functional requirements of the system and decided which related requirements we could add to improve the system.

| ID  | Short name  | Quality attribute | Description  |
|---|---|---|---|
| QR1  | Commands sanity checks | Reliability  | When a player issues a command, the syntax of the command shall be validated against the format specified in F6, such that the user’s command may always be recognised and use of the Fantasy Soccer game is consistent. |
| QR2  | Extensible Team | Maintainability  | The fantasy game shall be easily extendable in terms of drafting, trading and calculating scores for players such that future developers may change the drafting, trading and scoring systems to potentially extend the game to work with sports other than football. Also this means that developers may make subtle changes, such as altering how the system is scored.  |
| QR3  | Instantaneous results | Responsiveness  | Once the scores have been uploaded by the league manager, the results of the virtual matches will be available within one second. This is important to avoid significant lag in the system, making it more consistent for users. Technically, this delay depends on the system that the user is running the game on. |
| QR4  | Easy to Use | Usability | The command-line interface commands are easy to understand and intuitive for players to use. This is important to ensure that the game is accessible even to people who have not played soccer before. Any ambiguity on the commands should be explained in a help manual.|
| QR5  | Extensible Functions | Maintainability | The fantasy game shall be easily extendable in terms of what users can do, for example creating new leagues at any point. This will allow future developers to extend the game to add further functions (such as multiple leagues, improved readability etc)|
| QR6  | Seamless Functionality | Availability | The system will not crash, such that the game can be played seamlessly by the user. The consequences of a crash could be data loss, making the system less reliable. The system should handle a crash by restarting the system and reverting any statistics that have not been updated to what they previously were.|
| QR7  | Information Security | Security | Any information provided by users can not be accessed by other users. It should be secured in a database/csv that is not accessible to users.|
| QR8  | State Saving | Reliability | The state of the game will be maintained when the program is exited, such that the user can return to their game later. This file should not be able to be edited by users, and should be kept secure/ureadable.|



### Java libraries
Author(s): Nuriel Leve, Amanda Patterson, Dominic Smorra, Lucy Lawrence 


| Name (with link) | Description  |
|---|---|
| [opencsv](http://opencsv.sourceforge.net/)   | CSV parser that we will use for parsing a csv file of players in the premier league. We chose this among others because we wanted a very straightforward and simple parser. This seems to be a good balance between fulfilling all of our requirements and not being exceedingly complicated.  | 
| [JUnit](https://junit.org/junit5/)  | We will use it for testing various components of the application to ensure everything works smoothly. We chose this as it is a common testing framework. Some team members already have familiarity with this library, which will help as we aim to test rapidly and efficiently. We know the importance of testing and for this reason chose to include a framework like this one.  |
| [Time4J](https://github.com/MenoData/Time4J)  | We will use it for keeping track of real time throughout the season. Scheduling is very important in fantasy soccer. Drafts occur for only 24 hours, points are calculated every Sunday, and trading can only happen in a set period of time. For all of these reasons we knew we needed a way of keeping real time in our system. This seems to be a robust, but straightforward library, and as such, is ideal for our system. |
|[ASCII Table](https://github.com/vdmeer/asciitable)  | This may be helpful if we want to draw a table of the schedule of games. Fantasy Soccer is extremely statistically heavy. We want to give users the best experience possible, while still using a command line interface. We believe that utilizing this library may help us convey statistics to users in a readable manner. |
|[args4j](http://args4j.kohsuke.org/)  | This may help us parse command line arguments. As we are using a command-line interface, our program will clearly utilize many command line arguments. As with many of the other libraries we attempted to find a good balance between robustness and simplicity. We are open to the fact that as our project progresses we may need alternative command line processing power and may add additional libraries. However from where we stand now we believe this will be a suitable choice. |
