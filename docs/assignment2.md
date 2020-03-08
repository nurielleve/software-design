# Assignment 2
Maximum number of words for this document: 12000

**IMPORTANT**: In this assignment you will model the whole system. Within each of your models, you will have a *prescriptive intent* when representing the elements related to the feature you are implementing in this assignment, whereas the rest of the elements are used with a *descriptive intent*. In all your diagrams it is strongly suggested to used different colors for the prescriptive and descriptive parts of your models (this helps you in better reasoning on the level of detail needed in each part of the models and the instructors in knowing how to assess your models).   

**Format**: establish formatting conventions when describing your models in this document. For example, you style the name of each class in bold, whereas the attributes, operations, and associations as underlined text, objects are in italic, etc.

### Implemented feature

| ID  | Short name  | Description  |
|---|---|---|
| F1  | League Commands | The user can create and open/close the league to teams, set the schedule, and add statistics by issuing command-line commands with the following syntax:</br>**Note that these are only open to the league manager** </br> command-name [target-objects]*. The available command-names are the following: </br> create: ...</br>close: ...</br> open: … </br>setDraftOrder: … </br>setSchedule: ...</br>randomSchedule: … </br> addStatistics: … | 

Please note that we have since updated the F1. You can see our updated functional requirements in the assignment1 document on this branch. We implemented the scope of what was described in our original F1. 

### Used modeling tool
Draw.io

## Class diagram									
Author(s): Lucy, Nuriel, Amanda, Dominic 

![](images/FantasySoccerClassDiagram.png)

Author: Amanda 

For each class (and data type) in the class diagram you have to provide a paragraph providing the following information:
- Brief description about what it represents
- Brief description of the meaning of each attribute
- Brief description of the meaning of each operation
- Brief description of the meaning of each association involving it (each association can be described only once in this deliverable)



Maximum number of words for this section: 3000

## Object diagrams								
Author(s): `name of the team member(s) responsible for this section`

This chapter contains the description of a "snapshot" of the status of your system during its execution. 
This chapter is composed of a UML object diagram of your system, together with a textual description of its key elements.

`Figure representing the UML class diagram`
  
`Textual description`

Maximum number of words for this section: 1000

## State machine diagrams									
Author(s): `Dominic`

Color Coding: Blue - Prescriptive, Orange - Descriptive

State Machine 1: League Class

![](images/State-Machine-1.png)

Once the league is created, the league manager can then add up to 16 teams into the league. The league is kept open by the league manager until they decide that the teams or set. Once the teams are set, the league manager then closes the league not allowing any more teams to join the league. After that, the league will then either pass into the state of setting the schedule, or staging the draft if the order has been set. The order of these two states being completed does not matter. While in the schedule setting state the league manager calls the operation to create a schedule for all of the participating teams in the league. While in the drafting state, each team will take turns picking a player until they are all filled. After completing the draft and setting the schedule games can now be played. The league enters the cycle between the states of statistics becoming available for players, and winners being determined for each weekly match by the league manager entering the statistics. The league switches between these two states until all matches have been played. The league then enters its final state where the final standings between the teams can be viewed. After that the season has concluded and the league is over.


State Machine 2: Team Class

![](images/State-Machine-2.png)

Once a team is created, the team manager then has to draft their team. After the team is drafted, throughout the season the team manager has the ability to make changes to their team through dropping, adding, or trading players. These operations are done when the team manager inputs the command for which type of move to make. When the team is in the dropping state, it removes the chosen player from the team. After a player is dropped, teams usually add a different player. In order for the team to enter the state of adding a player, there has to be an open spot in the right position for the player to fill. Once the team does enter the adding state, the chosen player is then added to the team. The last operation that can be performed is trading. In order for a trade to happen, two teams have to agree to the trade. Once a team has entered the trading state, the team removes the players being traded away and adds the new players being received. After performing one of these roster moves, the team then returns to an updated state with the new team waiting for the next move. The team then enters its final state once the season has concluded and roster moves can no longer be made. 



## Sequence diagrams									
Author(s): Lucy, Nuriel

This chapter contains the specification of at least 2 UML sequence diagrams of your system, together with a textual description of all its elements. Here you have to focus on specific situations you want to describe. For example, you can describe the interaction of player when performing a key part of the videogame, during a typical execution scenario, in a special case that may happen (e.g., an error situation), when finalizing a fantasy soccer game, etc.

For each sequence diagram you have to provide:
- a title representing the specific situation you want to describe;
- a figure representing the sequence diagram;
- a textual description of all its elements in a narrative manner (you do not need to structure your description into tables in this case). We expect a detailed description of all the interaction partners, their exchanged messages, and the fragments of interaction where they are involved. For each sequence diagram we expect a description of about 300-500 words.

The goal of your sequence diagrams is both descriptive and prescriptive, so put the needed level of detail here, finding the right trade-off between understandability of the models and their precision.

User Validation Sequence Diagram

![](images/Seq-diagram-1.PNG)

This sequence diagram depicts the user validation method. The Main class interacts with database/csv file to receive, store and validate information about the users. In this diagram the user enters their username and unique ID, which is passed to the login method in the Main class. This method will pass the details to the database/csv, which contains the username/unique ID pairs. The validation is completed and checks whether the unique ID matches the username provided. The return message determines whether or not the details were valid (if they existed in the database/csv). At this point the diagram shows two alternatives - if the details were valid then the user is logged in and a ‘validated’ return message is sent back to the Main class, if not then the user does not exist. When the user is logged in, they have access to their teams in the league, if they are not logged in then they will either have to enter the correct unique ID or create a new user (this is not shown in the diagram).

Team Creation Sequence Diagram

![](images/Seq-diagram-2.PNG)

The Main and Team class pass messages containing input from the user, such as the name of the team and the player selections. The team class also sends return messages to confirm the completion of player selection. The team and league class interact through the actual instantiation of the player and team objects, which are both stored in the league object. The league class interacts with the main class by returning there in the program flow when a the player is selected and added to the team.
The main class is the point where the user gives information about the team they want to create, this information is passed to the team class. Once the team name is entered, the team is created and stored in the league class. The league class then returns confirmation to the team class that the team has been created and stored. The team then calls the select player operation which will allow the user to select the players on their team.
In the program, users take it in turns to select players so that the distribution of players is fair. This is not shown in the diagram for simplicity, but the user would have to wait between picking their player so that other users could pick too. The diagram shows that the program enters a loop, which repeats the selection process until the player number is 11 (at which the team is complete). When a player is selected, the selected player is passed in a message to the league class, which adds the player to the team (instantiates it and adds it to the team list). The league class then returns a confirmation message so that the program can return to the main class and another player can be selected. When the player number in the team stored in league reaches 11, a return message denoting that the team is complete is sent and the loop is exited.

Maximum number of words for this section: 3000

## Implementation									
Author(s): Amanda

In this chapter you will describe the following aspects of your project:
- Strategy that you followed when moving from the UML models to the implementation code: When moving from the UML models to the implementation code, the first thing that I did was to create the classes. I went through the class diagram and created classes corresponding with what we had modelled. I added all the attributes we had identified. The first operations I implemented were the getter and setter methods that we had identified as necessary. I now had the structure of the system set up, classes were made and attributes were set and usable. I then started work on the league manager commands. We had determined in the class diagram a series of commands that the league manager needed. They needed to be able to open and close their league, as well as add statistics and set the schedule of matches. I translated these commands into code and then moved onto the league commands. Additionally, during this time I was utilizing the object diagram. That was exceedingly helpful in wrapping my head around the bigger picture of our system. When I was lost or unsure where to go next I could remind myself what a ‘snapshot’ of this system would look like. From the league commands I moved onto how the user would actually interact with the system. In the main class of the system I set up the structure for inputting commands and that if no league had been set up yet the system would guide the user through setting up the system. This was fairly straight forward as I had already made use of the UML models to set up the structure of the system. This was just the final step in making it accessible to the user. 
- Key solutions that you applied when implementing your system (for example, how you implemented the syntax highlighting feature of your code snippet manager, how you manage fantasy soccer matches, etc.): One of the key solutions I applied when implementing the system was the scheduling of matches. This was rather tricky as the system had to be able to schedule a season of matches for anywhere between two and sixteen teams. We had decided on a round robin style of matches, where every team plays every other team and the team with the best record ‘wins’ in the end. I researched a round robin scheduling algorithm and decided on a system where I had a temporary array of all of the teams. One week of matches would consist of the first and the last teams playing each other and then the second and second to last teams, and so on, until the middle two teams were matched. If there were an odd number of teams, the middle team had a bye for that week. Each ‘week’ all but the first team in the array were shifted down one spot and the last was bumped to the front. The teams were again matched in the manner described above. This continued until every team had played every other team. For n teams, this meant n-1 weeks of play, if n was even, and n weeks of play, if n was odd. 
- The main java class is located in software-design/src/main/java/Main.java
- The Jar file for directly executing your system is in the repo in the file SoftwareDesignIdeas.jar
- The video is in software-design/docs/video_small.mov. I tried many attempts to embed it, but I believe there was an issue with my settings. 

<video src="video_small.mov" width="320" height="200" controls preload></video>



IMPORTANT: remember that your implementation must be consistent with your UML models. Also, your implementation must run without the need from any other external software or tool. Failing to meet this requirement means 0 points for the implementation part of your project.

Maximum number of words for this section: 2000

## References

References, if needed.
