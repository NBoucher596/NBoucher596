## The Last Tank
This project was for a Unity class I took at Old Dominion University. I used the Tanks Unity Learn project as a start of the project sinc eth goal was to make a major modification of the game. I decided to change the game from a hot seat player versus player to a player versus computer game similar to the Wii Play game: Tanks! <br>

### Computer Enemies
The largest change I made was changing the control of the enemies. I made a script that would drive, turn, and shoot based on certain conditions. The enemy tanks would always drive forward to pressure the player. If the tanks detected a collision box within the -45 degree to +45 degree arc, it would turn away. If a player was within a -30 degree to +30 degree arc in front of the enemy, they would look at the player and begin firing. I made the turn collision check happen before the shooting one to make sure the enemies would dodge most pieces of terrain. The major issue I had was making sure all different terrain models were high enough to be detected by the raycasting since I had them set to a standard height. The shots fired by the player were not able to be dodged by the enemies since the base speed is to high, but the enemies do try to turn away. <br>
### Tank Gun Changes
In the Unity Play project, the tank's gun fires in an arc resulting in the need for accurate charging of shell distance. I decided to switch to a flat linear height to make the shells behave like they do in Tanks! I decided to keep the charging ability to allow for faster shells but with the cost of automatically firing if it gets fully charged. Both the player and the computer enemies fire along the same trajeectory and the player can shoot the enemy bullets out of the air destorying both of the bullets. <br>
### Mines
I decided to add mines to the map that can affect both sides. The map was open and I was able to easily defeat the enemies so to increase the difficulty, I decided to add mines. They would deal a significant amount of damage. This required the player to drive carefully and allow fro some opprotunities to bait the enemies into running into them. This was added from a code perspecitive so does not have any animations by the end of the project. <br>
### Gameplay Effects
Some of the effects within the base game were a force adder that would trigger when the bullets would hit the tank. This made for an unintended, but hilarous effect where the player or enemy tanks will be pushed around and can go flying. This cartoony effect was very helpful for making the game more fun and engaging for the player. The other important aspect was the rapid pace of the game. I added a start button since the game would auto start. This allowed for the player to be ready before playing. The average time that most people lasted within the game was about a minute. While there were only three enemies, the impending assault from the enemies always moving forward put pressure on the player. <br>
### Future Proofing
This game was meant to be a demo, but I had spent some time thinking about how to make a level system with increasing waves of enemies. I would have a random number generator pick different numbers of enemies depending on the level. I made sure that the spawning system could easily have code added for additional levels, but for the demo only had one level to load. I also had the idea to potentially make alternative prefabs with different speeds and that was also taken into account when setting up the spawning system. If I were to revist this project, I would be able to add more levels and differnt types of enemies with different stats. <br>