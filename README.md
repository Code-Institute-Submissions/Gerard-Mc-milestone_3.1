## unfinished app
The app is intended to find out if a user's gpu is powerful enough to reach the minimun requirements of a game they want to get/play.
The user can choose from 200 of the most common and power ful GPUs from roughly the last 10 years. This list was taken from a site that rates gpus by power.

### What it can do

* Regex was used to make patterns that will extract, from steam api, gpus made by AMD and Nvidia that are less powerful than all gpus on the users gpu selection list.

If found on the selected games steam api doc, the user is told that they can play the game.

* If this doesn't find anything, a mongo collection holding over a large list gpus from nvidia, amd, and intel is searched.

If a match is found, the user is notified they can play the game because all gpus on this list are weaker than the 200 users gpus. 


* If the gpu is above that range, or is intel, regex patterns are used to find and format the gpus name and search the 200 user gpus on mongo.

Each GPU has a rating, and if the gpu selected by the user has a higher rating, then they are told they can play the game. If not, they are told they can't.

* Before all of above searches, a search to see if the selected game's requirements are in MB. These are old games and GPUs.

If the graphics card on the steam page is described in MB, it will be under 1gb, therefore less powerful than the user's, and the user is told they can play it.(This was meant to have a limit of 512mb incase od 1024mb cards.)

#### What it can and cab't do


- It can do the compare service and tell a user if their selected gpu can play a game


- If the game/gpu match result is positive, it stores the name of the game in an array within the GPU entity. This means next time this GPU/Game pair is checked, rather

than connected to the api and going through all the logic, it can just access the mongodb to get a quick answer.

- The user can register, sign in, and choose their gpu. A feature that was planned, was that when then user selected a gpu in there profile, 

they would see the array of all compatable games and be able to enter what frames per second they achieved playing it on their gpu, 

and see the average fps from all users on that particular game/gpu combo.

- Signed in users would have been able to see the average user FPS displayed on the results page after checking a combo.

 ####Testing

* Every variation of name from AMD Nvidea, and Intel was tested and seems to work well. 
