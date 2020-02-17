# Assignment 1


## Introduction									

For this project we’re targeting users who are interested in playing Fantasy Soccer within the Premier League. By interacting with the command-line interface, this user will be able to register in an open league or create a new one. Once the league is closed, in the 24 hour period after, there will be a draft. Users will form a team, or teams, of players composed of one goalkeeper, four defenders, four midfielders, and two attackers. They may choose players from any team within the Premier league; however, if there are multiple teams, a player may only be on one team at a time. The order teams may draft players in is set randomly, or can be chosen explicitly by the league manager. After the draft, they can then schedule games between members of that league. It is only the ‘league manager,’ or user who created the league, who is able to close the league and schedule the games between teams. This user will also have the option to opt for a randomized schedule, which would pair teams at random. Matches will be ‘played’ each Sunday according to the created schedule. A team will win the match if their total score is higher than their opponents. A score is tallied by adding up the points each player on their team has earned. In our system, player statistics will be provided manually by the league manager. Players are either on a team or in the pool of free players, and for 24 hours after the last game is played on Sunday, users can swap their players for players in the pool to improve their team. They can also ask for trades with other teams. When a team receives a trade request they can accept, deny, or send an alternative request. Users will also be able to see the current ranking of the teams in their league.  
 
We got inspiration from https://fantasy.premierleague.com/. We also looked at https://en.wikipedia.org/wiki/Fantasy_football_(association) for background knowledge.

## Features
Author(s): `name of the team member(s) responsible for this section`

<When defining both functional features and quality requirements, remember that you will need to come back to them in Assignments 2 and 3 and explicitly state how specific parts of models/implementation satisfy them.>

### Functional features

As a preamble to the table, you can discuss the main line of reasoning you applied for defining the functional features provided in the table.

| ID  | Short name  | Description  |
|---|---|---|
| F1  | Tags | Code snippets can be tagged via freely-defined labels called tags  |
| F2  | Commands  | The player can control the main character by issuing command-line commands following this syntax: `command-name [target-objects]*`. The available `command-names` are the following: <br/> - move: ... <br/> - use: ... <br/> - inspect: ... <br/> |
| F3  | Movements  | The main character shall move freely in the environment according  |
| F4  | ... | ... |

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
