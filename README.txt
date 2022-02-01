Animate Enemy and Enemy Float Scripts:
--------------------------------------

[WARNING]:
----------
THIS SCRIPT WILL EDIT AN ENEMY'S VITALITY, IQ, AND HOMESICKNESS STAT IN BATTLE.
IF ANY OF YOUR OR OTHER SCRIPTS EDIT THESE VALUES, THEN THESE SCRIPTS ARE
INCOMPATIBLE FOR YOUR HACK. FOR MOST HACKS, YOU WILL NOT NEED TO WORRY. ENJOY!!!



[Info]:
------
These bundle of scripts will allow you to have both animated and/or floating enemies.
The scripts that are focused on animating enemies are ones that are prefixed with
"Animate_Enemy". The same for floating enemies, they are prefixed with "Enemy_Float".
There are two scripts named "Additional_Enemy_Modifications" and 
"Battle_Game_Frame_Event_Listener" that allows both the animate and floating scripts to work.
Do not touch them if you don't know what you are doing.

To the more advance ROM Hacker though, you can attach a JSL() opcode to the 
"Battle_Game_Frame_Event_Listener" script so that the game can run your code per In-Game frame
during battle.

An idea would be like, say you want to palette swap an enemy every 60 frames so that you
can make the illusion that an enemy is glowing. Just create some code that changes the
palettes and only execute that on the 60th frame. You can then chuck that code address with 
a JSL() into the "Battle_Game_Frame_Event_Listener" script and you'd be done.



[Animate_Enemy]:
----------------
The scripts you'll want to focus on are:
  - Animate_Enemy_Main
    . This script contains configurations for each enemy to have their own animation.
	. If you do not want an enemy to animate, then leave their entry settings as is.
	  That is, leave everything 0 except for their "id" field.

You'll notice that there is another folder called "Animated Sprite Templates". This folder
contains all combinations of valid sprite and canvas sizes for each enemy. There are
sprites I used for testing and templates that contain the order of which those sprites
will advance to the next frame. The order is left to right, top to bottom.

However, keep in mind that there is a limit on how many sprites you can load into the game.
Keep track of the Canvas size you have for your enemy and the enemy groups they are in.
You can have an allocated maximum Canvas size of 128x192. All of your UNIQUE enemy canvas
must fit within that bound, I provided you a template for that as well so you can visually
see if you have enough space for that enemy to be in that enemy group.

For example: you can have four of the SAME 32x32 size sprites that has a 128x128 canvas size in an
enemy group since the total canvas space is less than 128x192. However, you cannot have
two UNIQUE 128x64 size sprites that takes up a 128x128 size canvas each since the total canvas
space would be 128x256, which we cannot fit within our graphically limitd 128x192 size canvas.

	  
	  
[Enemy_Float]:
--------------
The scripts you'll want to focus on are:
  - Enemy_Float_Main
    . This contains two config values you can redefine: amplitudeFraction and speedFraction.
	  The script contains info on what they do.
  - Enemy_Float_Enemy_ID_Table
    . This script contains a table for you to tell which enemy starts out floating at
	  the beginning of battle. It already contains some examples of which enemies will
	  start out floating by their IDs.