# FMOD Replacement Kit
A Project that aims to replace FMOD with the old audio scripts found in the Latest version of Pizza Tower

> [!IMPORTANT]
> This is currently in Active Development!
>
> Everything is subject to change

## So why do this
If you look at my Github Profile and my repos, you will see that I have made a Web Port of the Latest version of Pizza Tower, and that sound doesn't currently work on that port. So put 2 and 2 together and you'll know why I'm doing this

## Current Progress
This is currently just instructions to prepare the source code to Integrate the music files into the GMS2 project. You currently have to manually go through every
object and script to completly replace FMOD, and this has not been done yet.

## Downloads
Since the files are bigger than what Github allows, I will have to use Google Drive, and links will be added shortly

Current Instructions:

```
____            ____
|     |	   |   |       | /        _
|__   |    |   |       |/       _|_   _  _    __    __|
|     |    |   |       |\        |   | \/ |  |  |  |  |
|      \___|   |____   | \       |   |    |  |__|  |__|

EMBRACE OLD SCRIPTS

--------------------------------------------------------------------------------------------------------------

Using the FMOD Replacement Kit (FMOD-RK)

++++++++++++++++++++++++++++++++++++++++++++
The included Kit contains a .yyp file that |
has refrences to the music files, BUT it   |
also refrences some objects and scripts    |
that are only found in my slightly modified|
version of the Noise Update, so use the    |
Source Code in my Github if you want to use|
the Kit					   |
++++++++++++++++++++++++++++++++++++++++++++

1. Download my slightly modified version of Pizza Tower from my Github
2. Extract the ZIP Archive using 7zip (or WinRAR i guess)
3. Copy over the assets from FMOD-RK into the folder containing the Source Code

NOTE: You Need to Overwrite the .yyp file

4. Proceed to replacing FMOD functions

<--- 
If you want to replace FMOD on an older Pizza Tower build,
or just want to do this without the Kit for whatever reason,
Proceed to the Step Below
--->

--------------------------------------------------------------------------------------------------------------

To Extract Music Files from .BANK Files (No Kit Usage)

1. Download the "FMOD Bank Tools" Software from GameBanana
2. Place `music.bank` and `sfx.bank` files from your copy of the game into the `/bank` sub-directory
3. Start the Program and press "Extract"
4. Wait until completion, and then enter the `/wav` sub-directory (or whatever you picked)
5. Start Up your GMS 2 Runtime and load your Pizza Tower Source Code
6. Drag the `/music` and `/sfx` folders from your File Explorer into your `/Sounds` directory inside of GMS2
7. Proceed to replacing FMOD functions

WARNING!

GMS2 might try to modify objects and scripts once you've copied the files to it. 
DO NOT ALLOW GMS2 TO CHANGE THEM! ALL CHANGES HAVE TO BE DONE MANUALLY!

--------------------------------------------------------------------------------------------------------------

To replace FMOD functions with the old scripts
(functions found in `scr_sound.gml` & `scr_soundeffect.gml`)

	{ scr_sound(); } replaces { PLACEHOLDER } and is for Sounds

	{ scr_soundeffect(); } replaces { fmod_event_one_shot_3d("event:/", x, y); } and is for SFX

	{ scr_music(); } replaces { PLACEHOLDER } and is for Level Music

 <---  Music names go inside of the parenthesis ()  --->
<--- DO NOT INCLUDE THE CURLY BRACKETS WITH THE CODE --->

You have to replace these functions from almost every object/script in the game code, so good luck

--------------------------------------------------------------------------------------------------------------

ALL Functions within the Code

<--- Just an easy Cheat Sheet to make it a bit easier --->



fmod_event_one_shot_3d("event:/", x, y); -> scr_soundeffect();
[CONTINUE ME ON THIS LINE!!!]


--------------------------------------------------------------------------------------------------------------

Made by burnedpopcorn180 on Github

<--- The Guide was meant for the Noise Update, but could also apply for older versions --->


```
