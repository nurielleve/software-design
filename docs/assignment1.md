# Assignment 1
Maximum number of words for this document: 2500


## Introduction									
Author(s): Nuriel Leve, Amanda Patterson, Dominic Smorra, Lucy Lawrence 

For this project we’re targeting users who are interested in playing Fantasy Soccer within the Premier League. By interacting with the command-line interface, this user will be able to register in an open league or create a new one. Once the league is closed, in the 24 hour period after, there will be a draft. Users will form a team, or teams, of players composed of one goalkeeper, four defenders, four midfielders, and two attackers. They may choose players from any team within the Premier league; however, if there are multiple teams, a player may only be on one team at a time. The order teams may draft players in is set randomly, or can be chosen explicitly by the league manager. After the draft, they can then schedule games between members of that league. It is only the ‘league manager,’ or user who created the league, who is able to close the league and schedule the games between teams. This user will also have the option to opt for a randomized schedule, which would pair teams at random. Matches will be ‘played’ each Sunday according to the created schedule. A team will win the match if their total score is higher than their opponents. A score is tallied by adding up the points each player on their team has earned. In our system, player statistics will be provided manually by the league manager. Players are either on a team or in the pool of free players, and for 24 hours after the last game is played on Sunday, users can swap their players for players in the pool to improve their team. They can also ask for trades with other teams. When a team receives a trade request they can accept, deny, or send an alternative request. Users will also be able to see the current ranking of the teams in their league.  
 
We got inspiration from https://fantasy.premierleague.com/. We also looked at https://en.wikipedia.org/wiki/Fantasy_football_(association) for background knowledge.

## Features
Author(s): Nuriel Leve, Amanda Patterson, Dominic Smorra, Lucy Lawrence 


### Functional features

When defining the functional requirements we attempted to be as complete as possible. We went through all possible actions every type of user should be able to complete. We then brainstormed the other aspects the system must have in order for those actions to be completed. 

| ID  | Short name  | Description  |
|---|---|---|
| F1  | League Commands | The user can create and open/close the league to teams, set the schedule, and add statistics by issuing command-line commands with the following syntax: **Note that these are only open to the league manager** command-name [target-objects]*. The available command-names are the following: <br/> create: ... <br/> close: ... <br/> open: … <br/> setDraftOrder: … <br/> setSchedule: ... <br/> randomSchedule:: .. <br/> addStatistics: … |
| F2  | Team Commands  | The user can create a team, and add and remove players to their team by issuing command-line commands following this syntax: `command-name [target-objects]*`. The available `command-names` are the following: <br/> - create: ... <br/> - trade: ... <br/> - draft: ... <br/> - drop: ... |
| F3  | Statistic Viewing Commands  | It is highly important that everyone be able to see the statistics of the teams and rankings. We will have multiple ways of viewing stats: <br/> - viewRanking - This gives the overall ranking of the teams in the league. <br/> - viewSchedule - This gives the regular season schedule for the rest of the season. Teams must know who is playing who. <br/> - viewOpenPlayers - This gives a list of all players currently undrafted  <br/> - viewTeamPlayers [team name]* - This will print all players by team. If given a team name it will only print out the roster of that one team.  <br/> - getTeam [player name] - This will return the team name that the specified player is on, or ‘free’ if the player is undrafted. <br/> - getRecord [team name] [player name]* - This will return the record of a given team: who they played, the points they earned and whether it was a win or lose. If given a player name as well, the stats for that particular player are printed per game.   |
| F4  | Scoring | The points should be tallied every Sunday after the last game (and after the league manager inputs players statistics) and added via the scoring system to create individual team scores. |
| F5  | Manage Ranking | The points for each team will be listed and parsed through to create the ranking of the week, updating after every game (on Sunday). |
| F6  | Permission Status | Each team will have a unique id, their team name, but the league manager will have an additional password that they must use to access league commands. The league manager should be the only user allowed to make changes to their league. |
| F7  | Player Changes | The system should not allow any changes to teams except for the 24 hour window after the last game on Sunday. |
| F8  | Team Management  | The system will only keep track of players and their positions, only allowing teams of one goalkeeper, four defenders, four midfielders, and two attackers, and ensuring players are only on one team at a time.  |
| F9  | Player Trades | When a trade is sent from team to another in the form of the command: <br/> trade [sending team] [receiving team] [sending player] [receiving player] <br/> The receiving team may accept, y, deny, n, or deny and send an alternative trade in the same form. |
| F10  | Drafting | The system will automatically set a random order that drafting may take place in. Players are picked in a turn by turn basis and the order reverses each round. Only the team whose turn it is may draft a player. However, the league manager may override this with the setDraftOrder command found above. |


### Quality requirements
Author(s): `name of the team member(s) responsible for this section`

As a preamble to the table, you can discuss the main line of reasoning you followed for coming up with the quality requirements listed below.

| ID  | Short name  | Quality attribute | Description  |
|---|---|---|---|
| QR1  | Commands sanity checks | Reliability  | When the player issues a command, the syntax of the command shall always get validated against the format specified in F2 |
| QR2  | Extensible world | Maintainability  | The video game shall be easilty extendable in terms of levels, worlds, interaction points  |
| QR3  | Instantaneous results | Responsiveness  | Once the scores of all soccer players are provided by the user, the results of the virtual matches shall be available within 1 second |
| QR4  | ... | ... | ... |

Each quality requirement must be tagged with the corresponding quality attribute (see corresponding slides of the first lecture for knowing them).

Maximum number of words for this section: 1000

### Java libraries
Author(s): `name of the team member(s) responsible for this section`

| Name (with link) | Description  |
|---|---|
| [JFoenix](http://www.jfoenix.com/)  | Used for styling the user interface of the system. We chose it among others because ... | 
| [fastjson](https://github.com/alibaba/fastjson) | We will use it for reading and writing JSON configuration files containing the description of the levels of the videogame. We chose it because it is easy to configure and use from Java code and preliminary experiments makes us confident about its correct functioning... |
| ...  | ... |

Maximum number of words for this section: 500
