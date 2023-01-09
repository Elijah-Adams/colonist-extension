
# Explorer

![image](Screenshot.png)

Explorer parses the game transaction log in colonist.io to keep track of which player has which resources. 
No data is used to determine this that isn't clearly visible in the game.

In the event that a player robs another player, and you aren't involved in it, it may be unknown which resource
was stolen. Explorer will automatically keep track of this and show you. For example, "2 (1)" means that the player
has 2 of that resource, unless they stole one of that resource, in which case they would have 1 more (3 in total). As more plays are made, Explorer figures out what was in fact stolen and updates the table accordingly. 

**Note that Explorer will not run unless it's left open for the entire game.** Refreshing or reconnecting to the
game will clear the transaction log, making it impossible to re-calculate the player resource distribution.

<strike>Feel free to report any bug and/or PR a fix!</strike> Will not be maintaining, fork this please.
 

# Instructions

1. Download the source into a folder
2. Go to extensions on your chromium based browser
3. Enable developer mode
4. Load Unpacked
5. Select source folder

# Ethics
Is this ethical?

I was interested in exploring the importance of card counting in Catan for sciencific motivations. I believe the pursuit of science is blind to ethics and that science is not socially constructed but emergent from instincts.

Only information from the chat is used, which is avaliable to everyone. So this can be seen as and aid. The ethics of aids in online games is work for moral philosphers and users not programmers.

# Findings
Exact card counting from only the log is impossible for humans, there is combinatorial expolsion in the possibilities (a resource that is stolen can be restolen again). 

However, in practice you can rule posibilites based on what purchases a player didn't (couldn't) make. Therefore, human card counting is possibly even more effective that this plugin.

# Fork
The previous project was not matained and colonist.io changed their chat log breaking the parsing, which has been fixed in this fork.

Additionally, the resolving of stolen resources was incorrect, and obviously inadquate. This fork introduces a new method of computing the stolen resources.

This correctness comes at a cost. The previous developer was a true software engineer and his code was a pleasure to read, my hacks have degraded the code quality somewhat.

Also the theme has been changed to dark mode to work with the dark reader plugin.

# Debugging

Open the console in developer tools, and view the explorer.js script, setting a breakpoint at the end of the render function. Play a game against bots, run the code and compare the plugin computed total resources form the total resource cards displayed in game at each render update.

There still is a bug when parsing messages. To debug this plugin properly you would need to extract the resource card counts from the game, and then compare with the plugin computed resources
