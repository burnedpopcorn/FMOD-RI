# FMOD Replacement Instructions
A Project that aims to replace FMOD with the old audio scripts found in the Latest version of Pizza Tower

> [!IMPORTANT]
> This is not longer in active development, and is abandoned

## Current Progress
This is currently just instructions to prepare the source code to Integrate the music files into the GMS2 project. You currently have to manually go through every
object and script to completly replace FMOD, and this has not been done yet.

## Downloads
Since the files are bigger than what Github allows, I will have to use Google Drive

- [Extracted Audio for Step 1 of Instructions](https://drive.google.com/file/d/1ewwSq0ynbbuo-yBnyS5SaL6OKyhvjMy_/view?usp=sharing)
- [Recommended Source Code](https://drive.google.com/file/d/1gs1QJAjL5F7jAyJLj3esFuUiEPxVb1sq/view?usp=sharing)
> This Source Code has all of the sound files already integrated into the project for you, it just needs to have all the FMOD functions removed and replaced

## Music Configuration
All audio files in the ```music``` folder is set to ```Compressed - Not Streamed```, and other settings are left on default

All audio files in the ```sfx``` folder is set to ```Compressed - Streamed```, and other settings are left on default

## Current Instructions:

```
____            ____
|     |	   |   |       | /        _
|__   |    |   |       |/       _|_   _  _    __    __|
|     |    |   |       |\        |   | \/ |  |  |  |  |
|      \___|   |____   | \       |   |    |  |__|  |__|

EMBRACE OLD SCRIPTS

--------------------------------------------------------------------------------------------------------------

Step 1
Extracting Music Files from .BANK Files

1. Download the "FMOD Bank Tools" Software from GameBanana
2. Place `music.bank` and `sfx.bank` files from your copy of the game into the `/bank` sub-directory
3. Start the Program and press "Extract"
4. Wait until completion, and then enter the `/wav` sub-directory (or whatever you picked)
5. Start Up your GMS 2 Runtime and load your Pizza Tower Source Code
6. Drag the `/music` and `/sfx` folders from your File Explorer into your `/Sounds` directory inside of GMS2
7. Proceed to replacing FMOD functions

WARNING!

GMS2 might try get confused, as the music names can be the same as some variables in some scripts and objects
Please rename all music files with somw thing that will be absolutly unique, such as placing `mu_` or `sfx_`
before the rest of the file name

--------------------------------------------------------------------------------------------------------------

Step 2
To replace FMOD functions with the old scripts
(functions found in `scr_sound.gml` & `scr_soundeffect.gml`)

	{ scr_sound(); } replaces { PLACEHOLDER } and is for Sounds

	{ scr_soundeffect(); } replaces { fmod_event_one_shot_3d("event:/", x, y); } and is for SFX

	{ scr_music(); } replaces { PLACEHOLDER } and is for Level Music

 <---  Music names go inside of the parenthesis ()  --->
<--- DO NOT INCLUDE THE CURLY BRACKETS WITH THE CODE --->

You have to replace these functions from almost every object/script in the game code, so good luck

--------------------------------------------------------------------------------------------------------------

Step 3
Adding some Custom Functions

Add this to `scr_sound.gml`:
-------
function scr_soundrandom() // this custom funct should recreate FMOD Multi Instruments
{
	randomise();				// forces true random numbers
	var rand = irandom_range(1, argument0); // randomizes the first song and amount of songs specified
	scr_soundeffect(argument[rand]);	// selects and plays random song
}
------
Use this for any sounds that use Multi Instruments (you can find them below)
Example: scr_soundrandom(3, sfx_FileSelect1, sfx_FileSelect2, sfx_FileSelect3);
[First arg states there are 3 songs, rest of args are for sounds you want to include (you can add as many as you want)]

--------------------------------------------------------------------------------------------------------------

FMOD Music Bank Directories

<--- Just an easy Cheat Sheet to make it a bit easier to replace all FMOD functions --->

----------------------------------------+
Note that:				|
					|
- This hasn't been updated to reflect	|
the global name changes that is found	|
in the current WIP r7 Source Code, but	|
all names are very similar, so if you	|
have a brain, you should easily be able	|
to know what sounds are the same	|
					|
- [MI(SONGS HERE)] is when a Multi	|
Instrument is found, and those play	|
songs found in it randomly		|
					|
----------------------------------------+

FMOD Music Bank Directories		Corresponding .WAV Files

\music
   L-> \boss
	  L-> fakepep			= mu_fakepep
	  L-> fakepepambient		= PIZZA_TOWER_THyrzzryzryEME_SONG
	  L-> noise			= Pizza_Tower_OST_-_Pumpin_Hot_Stuff, (Noise) Pizza_Tower_OST_-_Doise_At_the_Door
	  L-> noisette			= noisette
	  L-> pepperman			= Pizza_Tower_OST_-_Pepperman_Strikes
	  L-> pizzaface			= unexpectancy1,2,3,remix
	  L-> vigilante			= mu_vigilante
	\soundtest
	  L-> bitethecrust		= Pizza_Tower_OST_-_Bite_the_Crust
	  L-> bye			= Pizza_Tower_OST_-_Bye_Bye_There
	  L-> celsius			= Pizza_Tower_-_Celcius_Troubles
	  L-> chateau			= Pizza_Tower_OST_-_Theres_a_Bone_in_my_Spaghetti
	  L-> coldspahetti		= Pizza_Tower_OST_-_Cold_Spaghetti
	  L-> creditsnoise		= New_Noise_Resolutionz_v4
	  L-> doise			= Pizza_Tower_OST_-_Doise_At_the_Door
	  L-> dungeon			= Pizza_Tower_-_Dungeon_Freakshow_v222
	  L-> engineer			= mu_industrial
	  L-> entrancenoise		= Pizza_Tower_OST_-_The_Noises_Jam-Packed_Radical_Anthem
	  L-> extraterrestrial		= Pizza_Tower_OST_-_Extraterrestrial_Wahwahs
	  L-> fakepep			= mu_fakepep
	  L-> forest1			= Pizza_Tower_-_mmm_yess_put_the_tree_on_my_pizza
	  L-> forest2			= mu_forest
	  L-> fridays			= mu_hub4
	  L-> funiculi			= mu_funiculi
	  L-> goodeatin			= mu_minigolf
	  L-> gustavo			= mu_gustavo
	  L-> halloweenpause		= Spacey_Pumpkins
	  L-> halloweenrace		= Final_The_Runner_10_15_2023_Halloween_Event_2023
	  L-> halloweenstart		= The_Bone_Rattler
	  L-> hip			= Pizza_Tower_OST_-_Hip_to_be_Italian
	  L-> hotspaghetti		= mu_medievalentrance
	  L-> intro			= Pizza_Tower_OST_-_Time_for_a_Smackdown
	  L-> kidsmenu			= Pizza_Tower_-_Whats_on_the_Kids_Menu
	  L-> lap			= mu_chase
	  L-> lap2noise			= World_Wide_Noise_v6_yo_how_many_times_am_i_just_gonna_keep_chan
	  L-> mayhem			= Pizza_Tower_OST_-_Pizza_Mayhem_Instrumental
	  L-> mayhem2			= 58 Pizza Mayhem
	  L-> meatphobia		= mu_dungeondepth
	  L-> mondays			= mu_hub
	  L-> mort			= mu_farm
	  L-> noise			= Pizza_Tower_OST_-_Pumpin_Hot_Stuff
	  L-> noisefinalescape		= noisefinalescape
	  L-> notime			= Pizza_Tower_OST_-_Receiding_Hairline_Celebration_Party
	  L-> oregano			= mu_desert
	  L-> pepperman			= Pizza_Tower_OST_-_Pepperman_Strikes
	  L-> pizzadeluxe		= mu_title
	  L-> pizzaheadnoise		= UNEXPECTANCY_CLASCYJITTO_I_GATCHA_PASSWORD_REMIX_v2
	  L-> pizzatime			= mu_pizzatime
	  L-> pizzatimenoise		= DISTASTEFUL_ANCHOVI_JC_RE-EDIT_v5c
	  L-> plains			= Pizza_Tower_OST_-_On_the_Rocks
	  L-> preheat			= 39 Don't Preheat Your Oven Because If You Do The Song Won't Pla
	  L-> putonashow		= mu_ruinremix
	  L-> saucemachine		= Pizza_Tower_OST_-_Peppinos_Sauce_Machine
	  L-> secretworld		= Secret_Lockin_v1a
	  L-> theatrical		= mu_ruin
	  L-> thousand			= mu_war
	  L-> thursdays			= pizza_tower_-_industrial_hub
	  L-> tombstone			= mu_graveyard
	  L-> toppins			= 59_BONUS_Choosing_the_Toppins
	  L-> tropical			= mu_beach
	  L-> tubular			= mu_sewer
	  L-> tuesdays			= Pizza_Tower_OST_-_Tuesdays
	  L-> tunnely			= Pizza_Tower_OST_-_Tunnely_Shimbers
	  L-> ufo			= mu_ufo
	  L-> unearthly			= Unearthly_Blues
	  L-> unexpectancy		= Pizza_Tower_OST_-_Unexpectancy_Part_1_of_3, 2_of_3, 3_of_3
	  L-> unexpectancy1		= Pizza_Tower_OST_-_Unexpectancy_Part_1_of_3
	  L-> unexpectancy2		= Pizza_Tower_OST_-_Unexpectancy_Part_2_of_3
	  L-> unexpectancy3		= Pizza_Tower_OST_-_Unexpectancy_Part_3_of_3
	  L-> vigilante			= mu_vigilante
	  L-> wayoftheitalian		= Pizza_Tower_OST_-_Way_of_the_Italian
	  L-> wednesdays		= mu_hub3
	  L-> yeehaw			= mu_saloon
	\w1
	  L-> dungeon			= Pizza_Tower_-_Dungeon_Freakshow_v222
	  L-> dungeondepth		= mu_dungeondepth
	  L-> dungeonsecret		= mu_dungeonsecret
	  L-> dungeontitle		= dungeon, (Noise) bloodsauce noise
	  L-> entrance			= Unearthly_Blues, PTentrance, (Noise) Pizza_Tower_OST_-_The_Noises_Jam-Packed_Radical_Anthem
	  L-> entrancesecret		= Pizza_Tower_-_Entrance_Secret_V1
	  L-> entrancetitle		= entrance, (Noise) entrance noise
	  L-> medieval			= mu_medivealentrance, Pizza_Tower_OST_-_Cold_Spaghetti, mu_medievalremix
	  L-> medievalsecret		= mu_medievalsecret
	  L-> medievaltitle		= medieval, (Noise) pizzascape noise
	  L-> ruin			= mu_ruin, mu_ruinremix
	  L-> ruinremix			= mu_ruinremix
	  L-> ruinsecret		= mu_ruinsecret
	  L-> ruintitle			= ruin, (Noise) ancient_noise
	\w2
	  L-> desert			= mu_desert, mu_ufo
	  L-> desertsecret		= mu_desertsecret
	  L-> deserttitle		= oregano, (Noise) oregano noise
	  L-> farm			= mu_farm, Pizza_Tower_-_Whats_on_the_Kids_Menu
	  L-> farmsecret		= mu_farmsecret
	  L-> farmtitle			= mort_farm, (Noise) mort the noise
	  L-> graveyard			= mu_graveyard
	  L-> graveyardsecret		= Pizza_Tower_-_An_Undead_Secret
	  L-> graveyardtitle		= graveyard, (Noise) wasteyard noise
	  L-> saloon			= mu_saloon
	  L-> saloonsecret		= mu_saloonsecret
	  L-> saloontitle		= saloon, (Noise) cowboy noise
	  L-> ufo			= mu_ufo
	\w3
	  L-> beach			= mu_beach
	  L-> beachsecret		= Pizza_Tower_-_A_Secret_in_the_Sands
	  L-> beachtitle		= beach, (Noise) plage noise
	  L-> forest			= Pizza_Tower_-_mmm_yess_put_the_tree_on_my_pizza, mu_gustavo, mu_forest
	  L-> forestsecret		= Pizza_Tower_-_A_Secret_in_The_Trees
	  L-> foresttitle		= gnome, (Noise) lario noise
	  L-> golf			= mu_minigolf
	  L-> golfsecret		= Pizza_Tower_-_A_Secret_Hole_in_One
	  L-> golftitle			= good_eating, (Noise) golf noise
	  L-> gustavo			= mu_gustavo
	  L-> space			= Pizza_Tower_OST_-_Extraterrestrial_Wahwahs
	  L-> spacesecret		= mu_pinballsecret
	  L-> spacetitle		= space, (Noise) deep dish noise
	\w4
	  L-> freezer			= 39 Don't Preheat Your Oven Because If You Do The Song Won't Pla, Pizza_Tower_-_Celcius_Troubles, Pizza_Tower_OST_-_On_the_Rocks
	  L-> freezersecret		= Pizza_Tower_-_A_Frozen_Secret
	  L-> freezertitle		= freezer, (Noise) freezer noise
	  L-> industrial		= mu_industrial, Pizza_Tower_OST_-_Peppinos_Sauce_Machine
	  L-> industrialsecret		= Pizza_Tower_-_An_Industry_Secret
	  L-> industrialtitle		= factory, (Noise) factory noise
	  L-> sewer			= mu_sewer
	  L-> sewersecret		= secret_sewer
	  L-> sewertitle		= sewer, (Noise) toxic noise
	  L-> street			= Pizza_Tower_OST_-_Bite_the_Crust, Pizza_Tower_OST_-_Way_of_the_Italian, dungeondepth
	  L-> streetsecret		= Pizza_Tower_-_A_Secret_In_These_Streets
	  L-> streettitle		= pig_city, (Noise) city_noise
	\w5
	  L-> chateau			= Pizza_Tower_OST_-_Theres_a_Bone_in_my_Spaghetti
	  L-> chateautitle		= chateau, (Noise) scary noise
	  L-> finalhallway		= pt_scary_ambient_draft_1
	  L-> kidsparty			= Pizza_Tower_OST_-_Tunnely_Shimbers
	  L-> kidspartychase		= CHASE_THEME_LOOP
	  L-> kidspartysecret		= Pizza_Tower_-_A_Secret_You_Dont_Want_To_Find
	  L-> kidspartytitle		= kids_party, (Noise) kidsparty noise
	  L-> war			= mu_war
	  L-> warsecret			= Pizza_Tower_-_A_War_Secret
	  L-> wartitle			= war
	characterselect			= 64 BONUS Move It, Boy
	chase				= mu_chase
	credits				= Pizza_Tower_-_Receiding_Hairline_Celebration_Party, (Noise) New_Noise_Resolutionz_v4
	ending				= windloop
	finalescape			= Pizza_Tower_OST_-_Bye_Bye_There, (Noise) byebyethere_remix_2_new_mix
	finalrank			= dungeondepth, Pizza_Tower_OST_-_Hip_to_be_Italian
	halloween2023			= The_Bone_Rattler, Final_the_Runner_10_15_2023_Halloween_Event_2023
	halloweenpause			= Spacey_Pumpkins
	hub				= mu_hub, Pizza_Tower_OST_-_Tuesday, mu_hub3, pizza_tower_-_industrial_hub, mu_hub4
	intro				= Pizza_Tower_OST_-_Time_for_a_Smackdown
	medley				= [A] mu_minigolf, [B] mu_funiculi, [C] 59_BONUS_Choosing_the_Toppins
	noiseunlocked			= 62 BONUS The Noise
	pause				= Pizza_Tower_-_Leaning_Dream
	peppinohouse			= mu_funiculi
	pillarmusic			= dungeondepth
	pizzatime			= mu_pizzatime, mu_chase, (Noise) DISTASTEFUL_ANCHOVI_JC_RE-EDIT_v5c, World_Wide_Noise_v6_yo_how_many_times_am_i_just_gonna_keep_chan
	pizzatimenoise			= DISTASTEFUL_ANCHOVI_JC_RE-EDIT_v5c, World_Wide_Noise_v6_yo_how_many_times_am_i_just_gonna_keep_chan
	rank				= mu_ranks, mu_ranka, mu_rankb, mu_rankc, mu_rankd, prank
	secretworld			= Secret_Lockin_v1a
	secretworldtitle		= secret_level_intro, (Noise) secret noise
	timesup				= Pizza_Tower_OST_-_Your_Fat_Ass_Slows_You_Down
	timesup-sfx			= 210_COOK, mu_timesup
	timesupalt			= mu_timesup
	title				= mu_title
	tutorial			= mu_funiculi
\sfx
   L-> \antigrav
	  L-> bump			= [MI(antigravbump1, antigravbump2, antigravbump3)]
	  L-> end			= antigravend
	  L-> start			= antigravstart
	\barrel
	  L-> bump			= [MI(barrelbump1, 2, 3, 4, 5, 6, 7)]
	  L-> slide			= barrel
	  L-> slope			= barrelslopejump
	  L-> start			= barrelstart
	\boxxed
	  L-> flap			= [MI(boxxedflap1, 2, 3, 4)]
	  L-> spin			= boxxedspin
	  L-> step			= [MI(boxxedstep1, 2, 3, 4)]
	\cheese
	  L-> ball			= cheeseball
	  L-> ground			= [MI(cheesestep1, 2, 3, 4)]
	  L-> jump			= [MI(cheesejump1, 2, 3, 4)], sfx_jump
	  L-> step			= [MI(cheeseground1, 2, 3, 4)]
	\ending
	  L-> johnending		= johnending1, johnending2, johnending3, GET_BOSS_KEY, Pizzahead1, mrstickhat, boxxedspin
	  L-> johnending-mu		= mu_ranks, music_null
	  L-> star			= rankup3
	  L-> towercollapse		= bossgaterise, sfx_escaperumble
	  L-> towercollapsetrack	= Voice-13, Voice-05, BrickSniff1
	  L-> towercollapsetrack-mu	= Pizza_Tower_-_Pizza_Pie-ing_slight_remaster
	\enemies
	  L-> alarm			= alarm
	  L-> axethrow			= axethrow
	  L-> badrat			= BAD_RATS_WOOSH
	  L-> banditochicken		= banditochicken
	  L-> batwing			= batwing
	  L-> burp			= burp
	  L-> cannongoblin		= CANNON_GOBLINS_FIRE
	  L-> charge			= EnemyCharge
	  L-> cloneattack		= fakepepbodyslam
	  L-> comingoutground		= comingoutground, gravecorpsestart
	  L-> coughing			= coughing
	  L-> demoncharge		= firesound
	  L-> demonsurprise		= demonsuprise
	  L-> escapespawn		= sfx_escapespawn
	  L-> fakesanta			= santa
	  L-> hamkuffgrab		= CITY_PIG_GRAB
	  L-> homing			= homing
	  L-> johndead			= JOHN_PILLAR_IMPACT
	  L-> johnghost			= johnghost
	  L-> jumpscare			= jumpscare
	  L-> kill			= sfx_killenemy
	  L-> killingblow		= sfx_killingblow
	  L-> minijohnpunch		= SEWER_CUTOUT_NINJA_SLAP
	  L-> ninjakicks		= SEWER_CUTOUT_NINJA_SLAP x9
	  L-> noisegoblinbow		= NoiseGoblinBow
	  L-> pickledance		= pickledance
	  L-> piranha			= piranha
	  L-> pizzardelectricity	= PizzardElectricity
	  L-> presentfall		= presentfall
	  L-> projectile		= sfx_enemyprojectile
	  L-> rancherpistol		= RANCHER_PISTOL_START
	  L-> robotslapsteam		= robotslapsteam
	  L-> stomp			= sfx_stompenemy
	  L-> treasureguy		= TREASURE_GUY_APPEAR
	  L-> tribaldance		= TRIBALDANCE
	  L-> ufolivelaser		= ufolivelaser
	\fakepep
	  L-> bodyslam			= fakepepbodyslam
	  L-> bodyslamclone		= fakepepbodyslam
	  L-> chase			= fakepepchase
	  L-> chasebegin		= JOHN_PILLAR_IMPACT
	  L-> deform			= fakepepdeform
	  L-> deformclone		= fakepepdeform
	  L-> flailing			= fakepepflailing
	  L-> grab			= fakepepgrab
	  L-> headoff			= fakepepheadoff
	  L-> headthrow			= fakepepheadthrow
	  L-> mach			= fakepepmach
	  L-> machclone			= fakepepmach
	  L-> reform			= fakepepreform
	  L-> reformclone		= fakepepreform
	  L-> step			= fakepepstep
	  L-> superjump			= fakepepsuperjump1
	  L-> superjumpclone		= fakepepsuperjump1
	  L-> superjumpclonerelease	= fakepepsuperjump2
	  L-> taunt			= fakepeptaunt
	\firemouth
	  L-> dash			= trashjump2
	  L-> jump			= sfx_firemouthdash
	  L-> start			= sfx_firemouthstart
	\hub
	  L-> gusbrickfightball		= [MI(sfx_killingblow, sfx_punch)]
	  L-> gusrun			= sfx_mach1
	\intro
	  L-> pepgustavointro		= PepGustavoCliff, (Noise) Noise_Intro_2
	\kingghost
	  L-> loop			= kingghostloop
	  L-> move			= kingghostmove
	\knight
	  L-> down			= sfx_knightdown
	  L-> lose			= sfx_loseknight
	  L-> slide			= sfx_knightslide
	  L-> start			= sfx_knightsword
	  L-> thunder			= sfx_becomeknight
	\misc
	  L-> ballonpop			= nosepop
	  L-> beerbreak			= beerbreak
	  L-> beerhit			= beerhit
	  L-> bellcollect		= bellcollectsmall
	  L-> bellcollectbig		= bellcollectbig
	  L-> blackoutpunch		= blackoutpunch
	  L-> bossbeaten		= BOSS_BEATEN_JINGLE, (Noise) noise_defeat_boss
	  L-> bossdefeattonk		= bossdefeattonk
	  L-> bosskey			= GET_BOSS_KEY
	  L-> bossvulnerable		= bossvulnerable
	  L-> bottlepop			= bottlepop
	  L-> breakblock		= [MI(sfx_breakblock1, 2)]
	  L-> breakdance		= sfx_breakdance
	  L-> breakdancemusic		= sfx_breakdancemusic
	  L-> breakice			= [MI(icebreak2, 3)]
	  L-> breakicebig		= icebreakbig
	  L-> breakmetal		= sfx_breakmetal
	  L-> bubblestation		= Bubblestation, PizzardElectricity
	  L-> captaingoblincrosshair	= cannonball
	  L-> captaingoblinshoot	= [MI(cannonballshot1, 2, 3, 4)]
	  L-> cardcollect		= CARD_COLLECT
	  L-> cardflip			= sfx_cardflip
	  L-> checkpoint		= Checkpoint
	  L-> cheers			= Cheers
	  L-> clotheswitch		= switch1
	  L-> collect			= sfx_collect
	  L-> collectgiantpizza		= sfx_collectgiantpizza
	  L-> collectpizza		= sfx_collectpizza
	  L-> collecttoppin		= sfx_collecttoppin
	  L-> comboend			= sfx_comboend
	  L-> computerswitch		= computerswitch
	  L-> computertouch		= computertouch
	  L-> cow			= Cow
	  L-> cowkick			= sfx_cowkick, cannonballshoot1
	  L-> cross			= cross
	  L-> dashpad			= dashpad
	  L-> detransfo			= Detransfo
	  L-> door			= sfx_door
	  L-> elevatorsqueak		= [MI(elevatorsqueak, elevatorsqueak2)]
	  L-> elevatorstart		= elevatording
	  L-> escaperumble		= sfx_escaperumble
	  L-> explosion			= sfx_explosion
	  L-> foundtreasure		= TREASURE_FIND
	  L-> galloping			= galloping
	  L-> gaterise			= bossgaterise, sfx_breakblock1, sfx_breakblock2
	  L-> golfbump			= [MI(golfbump1, 2, 3)]
	  L-> golfjingle		= JINGLE_0, JINGLE_1, JINGLE_2, JINGLE_3
	  L-> golfpunch			= sfx_punch, [MI(golfbump1, golfbump2, golfbump3)]
	  L-> halloweenpumpkin		= pumpkin
	  L-> hamkuff			= hamkuff1, hamkuff2, hamkuff3
	  L-> honkhonk			= honkhonk
	  L-> instanttemp		= instanttemp
	  L-> jumpscare			= [MI(sfx_scream1, sfx_scream4, sfx_scream7)]
	  L-> kashing			= Kashing
	  L-> kashingcombo		= Kashing, sfx_comboend
	  L-> keyunlock			= keyunlock
	  L-> lap2start			= Lap2
	  L-> lapcenter			= sfx_lapenter
	  L-> lapexit			= sfx_lapexit
	  L-> loserace			= LOSE_RACE
	  L-> mine			= sfx_mine
	  L-> mrpinch			= mrpinch1, mrpinch2
	  L-> mrstickhat		= mrstickhat
	  L-> mushroombounce		= [MI(mushroom1, 2, 3)]
	  L-> nosepop			= nosepop
	  L-> pepbotkick		= pepbotkick
	  L-> pepgusswitch		= PEPPINO_GUSTAVO_SWITCHING_SONG
	  L-> piranhabite		= piranhabite
	  L-> policesiren		= policesiren
	  L-> racestart			= sfx_racestart
	  L-> rockbreak			= rockbreak
	  L-> secretenter		= sfx_secretenter
	  L-> secretexit		= sfx_secretexit
	  L-> secretfound		= sfx_secretfound
	  L-> sniff			= pizzapepper
	  L-> sniffbump			= sniff2
	  L-> spaceship			= spaceship, Scream, noisescream
	  L-> superspring		= trashjump1, cannonballshoot1, mushroom1
	  L-> switchend			= switch2
	  L-> switchstart		= switch1
	  L-> taxibeep			= sfx_taxi1
	  L-> taximove			= sfx_taxi2
	  L-> teleporterend		= teleporter2
	  L-> teleporterstart		= teleporter1
	  L-> thundercloud		= thundercloud2, sfx_thundercloud
	  L-> timerbegin		= sfx_timerbegin
	  L-> timercount		= sfx_timercount
	  L-> timerend			= sfx_timerend
	  L-> toppingot			= SEWER_CUTOUT_NINJA_SLAP
	  L-> toppinhelp		= toppinhelp
	  L-> transfo			= Transfo
	  L-> trashjump1		= trashjump1
	  L-> trashjump2		= trashjump2
	  L-> treasure			= TREASURE_FIND
	  L-> ufo			= UFO
	  L-> ventilator		= sfx_ventilator
	  L-> versusscreen		= boss_introduction
	  L-> waterslide		= waterslide
	  L-> watersildesplash		= [MI(watersildesplash, watersildesplash2, watersildesplash3)]
	  L-> watersplash		= watesplash
	  L-> windloop			= windloop
	  L-> winrace			= WIN_RACE
	\monsters
	  L-> cheeseloop		= fakepepchase x2, monstergoop
	  L-> puppetfly			= waterslide
	  L-> robotstep			= metallicstep
	  L-> sausagestep		= guswalljump1
	\mort
	  L-> cube			= MortCube
	  L-> doublejump		= mortdoublejump
	  L-> down			= mortdown
	  L-> hook			= morthook, SEWER_CUTOUT_NINJA_SLAP
	  L-> mortdead			= MortDead
	  L-> mortpickup		= MortPickup1
	  L-> mortslap			= SEWER_CUTOUT_NINJA_SLAP
	  L-> side			= mortside
	  L-> throw			= mortthrowstart
	  L-> throwcatch		= mortcatch
	  L-> throwloop			= mortthrow
	  L-> up			= mortup
	\noise
	  L-> ballon			= noiseballon
	  L-> bombbounce		= noisebombbounce
	  L-> droptrap			= groundpoundloop
	  L-> fightball			= sfx_killingblow, [MI(noisefightball1, 2, 3, 4, 5, 6, 7, 8, 9)]
	  L-> giantballon1		= groundpoundloop
	  L-> giantballon2		= pistolshot, sfx_explosion, sfx_breakmetal, cannonballshoot1, uppercut
	  L-> jetpackloop		= noisejetpack
	  L-> jetpackspin		= noisejetpackspin
	  L-> jetpackstart		= noisejetpackstart
	  L-> machslide			= noisejetpackstart
	  L-> noisecrusher		= noisecrusher
	  L-> pogo			= sfx_Npogo3
	  L-> skatealone		= noiseskatealone
	  L-> skateloop			= noiseskatealone
	  L-> skatestart		= noiseskatestart
	  L-> skateturn			= noisejetpackstart x2
	  L-> spin			= sfx_Nspin
	  L-> woag			= sfx_noisewoah
	\noisette
	  L-> collect			= noisettevoice1
	  L-> kiss			= noisette_kiss
	  L-> voice1			= noisettevoice1
	  L-> voice2			= noisettevoice2
	\pep
	  L-> animatronic		= animatronic
	  L-> backslide			= Slideground
	  L-> bombbounce		= bombbounce
	  L-> bombfuse			= fuse
	  L-> box			= sfx_box
	  L-> break			= sfx_break
	  L-> bumpwall			= sfx_bumpwall
	  L-> burn			= firesound
	  L-> cheesefloor		= sfx_cheesejump
	  L-> cheesejump		= sfx_cheesefloor
	  L-> cross			= crossloop
	  L-> crouchslide		= dive
	  L-> dive			= dive
	  L-> fireass			= Fireass
	  L-> freefall			= groundpoundstart, groundpoundloop
	  L-> ghostintro		= GhostPepIntro, sfx_killenemy
	  L-> ghostspeed		= GHOST_SPEED_0, GHOST_SPEED_1, GHOST_SPEED_2
	  L-> gotsupertaunt		= supertauntnotif
	  L-> grabcancel		= sfx_rollgetup
	  L-> gravecorpse		= gravecorpse
	  L-> gravecorpsestart		= gravecorpsestart
	  L-> groundpound		= sfx_groundpound
	  L-> hitwall			= 
	  L-> hurt			= sfx_pephurt, hurt
	  L-> jetpackjump		= jetpackjump
	  L-> johnghost			= sfx_johnghost
	  L-> jump			= sfx_jump, jump
	  L-> mach			= sfx_mach1, sfx_mach2, sfx_mach3, sfx_mach4
	  L-> mach2bump			= [MI(mach2bump1, 2, 3, 4)]
	  L-> machpunch			= sfx_machpunch
	  L-> machroll			= machroll
	  L-> machslide			= sfx_machslide
	  L-> machslideboost		= sfx_machslideboost
	  L-> parry			= sfx_parry
	  L-> pistolshot		= pistolshot
	  L-> pistolstart		= pistolstart
	  L-> pizzapepper		= pizzapepper
	  L-> pray			= sfx_pray
	  L-> punch			= sfx_punch
	  L-> rampjump			= groundpoundstart
	  L-> revolverBIGshot		= cannonballshoot1
	  L-> revolvercharge		= pistolstart
	  L-> rollgetup			= sfx_rollgetup
	  L-> screamboss		= Scream, (Noise) noisescream
	  L-> shotgungot		= sfx_shotgungot
	  L-> shotgunload		= shotgunload, shotgungot
	  L-> shotgunshot		= shotgunshot
	  L-> slip			= bananaslip
	  L-> slipbump			= [MI(slipnslide1, 2, 3, 4, 5, 6, 7, 8)
	  L-> slipend			= [MI(slipnslideend1, 2, 3)]
	  L-> spin			= SEWER_CUTOUT_NINJA_SLAP
	  L-> splat			= golfbump1 x2
	  L-> step			= sfx_step
	  L-> stepinshit		= SEWER_STEP_IN_SHIT
	  L-> superjump			= sfx_superjumpprep, sfx_superjumphold, sfx_superjumprelease
	  L-> superjumpcancel		= superjumpcancel, dive, uppercut x2
	  L-> supertaunt		= sfx_taunt
	  L-> suplexdash		= sfx_suplexdash
	  L-> taunt			= sfx_taunt
	  L-> tumble			= sfx_tumble2, sfx_tumble3, sfx_tumble4
	  L-> uppercut			= uppercut2
	\pepperman
	  L-> artdude			= peppermanartdude
	  L-> groundpound		= groundpoundstart, groundpoundloop
	  L-> groundpoundbump		= [MI(mach2bump1, 2, 3, 4)]
	  L-> groundpoundjump		= peppermanjump
	  L-> knightappear		= gravecorpsestart
	  L-> knightslide		= sfx_knightslide
	  L-> shoulderbash		= ratmountgroundpound
	  L-> shrink			= peppermanshrink
	  L-> statueappear		= gravecorpse
	  L-> statuedestroy		= icebreak1, [MI(sfx_breakblock1, 2)]
	  L-> turn			= peppermanturn, sfx_machslideboost
	\pipe
	  L-> bump			= [MI(pipebump1, 2, 3, 4)]
	  L-> end			= pipe2, sfx_killingblow, pipe1
	  L-> start			= pipe2
	\pizzaface
	  L-> jump			= pizzafacejump
	  L-> laugh			= PizzafaceLaugh2
	  L-> moving			= PizzafaceMoving
	  L-> open			= pizzafaceopen, ratgrab1
	  L-> ram			= pizzafaceram1, groundpoundloop, pizzafaceram2
	  L-> shower			= pizzafaceshower1, pizzafaceshower2, pizzafaceshower3, pizzafaceshower4, pizzafaceshower5
	  L-> spit			= pizzafacespit
	\pizzahead
	  L-> beatdown			= sfx_punch
	  L-> bigpunch			= axethrow
	  L-> bigpunchstart		= vigiuzijump
	  L-> cog			= ratmountball
	  L-> finale			= groundpoundstart, groundpoundloop, sfx_mach4
	  L-> finaleexplosion		= vigicowstomp, sfx_explosion
	  L-> fishing			= dive, pizzaheadfishingbase
	  L-> giantstomp		= vigiuzijump
	  L-> grablevel			= bossgaterise
	  L-> haywire			= pizzaheadhaywire
	  L-> jump			= pizzafacejump
	  L-> medievalbringup		= mortside, sfx_escaperumble
	  L-> medievalprojectile	= axethrow
	  L-> ratball			= axethrow
	  L-> recover			= GET_BOSS_KEY
	  L-> spin			= boxxedspin
	  L-> step			= pizzaheadstep
	  L-> swinging			= ratmountgroundpound
	  L-> swingstart		= vigithrow
	  L-> throw			= vigithrow
	  L-> thunder			= gravecorpsestart, kingghostmove
	  L-> tvbounce			= sfx_killingblow, TVStatic, vigicowstomp
	  L-> tvthrow			= pizzaheadgrabtv
	  L-> uzi			= sfx_killingblow
	\playerN
	  L-> airspin			= airspin
	  L-> animatronic		= flies
	  L-> balloonflap		= balloonflap
	  L-> bombthrow			= bombthrow, vigithrow
	  L-> bossdeath			= bossdeath
	  L-> break			= noisejetpackstart
	  L-> bucket			= bucket
	  L-> divebomb			= tornado
	  L-> doiserock			= doiserock
	  L-> doublejump		= doublejump2, doublejump
	  L-> fightball			= [MI(noisefightball1, 2, 3, 4, 5, 6, 7, 8, 9)]  , sfx_killingblow
	  L-> finale_explosion		= finaleexplosion, sfx_escaperumble, sfx_explosion
	  L-> finale_outbomb		= NoiseCrazy_1
	  L-> finale_pizzahead		= finale2 x2
	  L-> finaljudgement_drumroll	= finaljudgement2
	  L-> finaljudgement_start	= finaljudgement1
	  L-> finaljudgement_verdict	= finaljudgementbad, finaljudgementgood
	  L-> fireball			= noise_fireballs, noisebombbounce
	  L-> firemouthjump		= firemouth
	  L-> freezerintro		= noise_freezerintro
	  L-> ghostdash			= ghostdash1, ghostdash2, ghostdash3
	  L-> giantbombthrow		= mortthrowsstart
	  L-> horseydead		= horsedead
	  L-> lionscream		= noisedemonscream
	  L-> mach			= mach x3, mach2step x3
	  L-> machslide			= noisejetpack x2
	  L-> minigunloop		= minigunloop
	  L-> minigunshot		= [MI(minigunshot1, 2, 3, 4)]  , [MI(minigun1, 2, 3, 4)]
	  L-> minijetpack		= minijetpack
	  L-> piggrab			= pigthrow
	  L-> pigthrow			= pigthrow2
	  L-> punch			= [MI(punch1, 2)]
	  L-> rushdownend		= [MI(rushdownend1, 2)]  , rushdownendbase
	  L-> rushdownhit		= rushdown2
	  L-> rushdownloop		= rushdown1
	  L-> superjump			= sjump
	  L-> superjumprelease		= sjump
	  L-> supernoiseeffect		= supernoiseeffect
	  L-> supernoisescream		= supernoise
	  L-> titlecard			= [MI(titlecard1, 2, 3)]
	  L-> wallbounce		= machcancel2, skateboardjump
	  L-> wallbounceland		= machcancelland, skateboardland
	\rat
	  L-> deflate			= CITY_RAT_BALOON_DEFLATE
	  L-> deflateeat		= ratdeflat2, CITY_RAT_BALOON_DEFLATE
	  L-> grab			= ratgrab1
	  L-> grabeat			= ratgrab2
	  L-> ratbowling		= ratbowling
	  L-> ratdead			= ratgrab1 x3, RatDead
	  L-> ratsniff			= RatSniff
	\ratmount
	  L-> ball			= ratmountball
	  L-> groundpound		= ratmountgroundpound
	  L-> mach			= ratmount2air
	  L-> punch			= axethrow
	  L-> walljump1			= guswalljump1
	  L-> walljump2			= guswalljump2
	\ui
	  L-> angelmove			= MenuMove, sfx_step
	  L-> back			= MenuBack
	  L-> bombfuse			= fuse
	  L-> comboup			= [MI(comboup1, 2, 4)]
	  L-> fileselect		= [MI(FileSelect1, 2, 3)]
	  L-> fileselectN		= selectscream
	  L-> lightswitch		= MenuLightswitch
	  L-> menuexplosions		= menuexplosions, sfx_explosion x4
	  L-> noiseselect		= Noise2, sfx_collectpizza
	  L-> pepselect			= Voice-18, sfx_collectpizza
	  L-> percentagemove		= rankup1
	  L-> rankdown			= rankdown5, rankdown4, rankdown3, rankdown2, rankdown1
	  L-> rankup			= rankup1, rankup2, rankup3, rankup4, rankup5
	  L-> select			= [MI(MenuSelect1, 2, 3)]
	  L-> slider			= Scream x2
	  L-> slidermusic		= Scream x2
	  L-> slidersfx			= Scream x2
	  L-> slidersfxmaster		= Scream x2
	  L-> step			= sfx_step
	  L-> switchchardown		= switchchar2
	  L-> switchcharup		= switchchar1
	  L-> tvstatic			= TVStatic
	  L-> tvswitch			= TVswitch
	  L-> tvswitchback		= TVswitchback
	  L-> wartimer			= WarTimer
	  L-> wartimerup		= WarTimerUp
	\vigilante
	  L-> bazookashoot		= cannonballshoot1, cannonballshoot2
	  L-> bazookatrail		= bossgaterise
	  L-> cowdead			= Cow x2, SEWER_STEP_IN_SHIT x3, sfx_explosion
	  L-> cowstomp			= vigicowstomp
	  L-> finalshot			= sfx_killingblow, sfx_racestart
	  L-> flamestart		= vigiflamestart
	  L-> flamethrower		= vigiflame
	  L-> ghostloop			= ghostambient
	  L-> mach1			= vigistep
	  L-> order			= vigiorder
	  L-> slide			= vigislide
	  L-> throw			= vigithrow
	  L-> uzijump			= vigiuzijump
	  L-> uziprep			= groundpoundloop
	  L-> uzishoot			= sfx_killingblow
	\voice
	  L-> brickok			= [MI(BrickSniff1, 2, 3  , BrickYodeling)]
	  L-> enemyrarescream		= [MI(enemyrarescream, enemyrarescream2)]
	  L-> fakepepnegative		= [MI(fakepepnegative1, 2)]
	  L-> fakepeppositive		= [MI(fakepeppositive1, 2, 3)]
	  L-> fakepepscream		= fakepepscream
	  L-> geromegot			= GeromeGot
	  L-> gushurt			= [MI(Voice-01, Voice-02)]
	  L-> gusok			= [MI(Voice-04, 05, 06, 07, 08, 09)]
	  L-> hurt			= [MI(Voice-10, Voice-11)]
	  L-> mrstick			= [MI(MrStick1, MrStick4, MrStick5)]
	  L-> mrsticklaugh		= [MI(MrStick2, MrStick3)]
	  L-> muffledscream		= Scream
	  L-> myea			= [MI(Voice-18, Voice-19, Voice-20, Voice-14, Voice-21)]
	  L-> noisenegative		= [MI((Noise1, 2, 4) x2)]
	  L-> noisepositive		= [MI((Noise2, 3, 5, 6) x2)]
	  L-> noisescream		= noisescream x2
	  L-> ok			= [MI(Voice-13, 20, 21)]
	  L-> outtransfo		= [MI(Voice-18, 19, 12)], Noise4
	  L-> peppermanlaugh		= PeppermanLaugh
	  L-> peppermanscared		= PeppermanScared
	  L-> peppermansnicker		= PeppermanSnicker
	  L-> peppinoangryscream	= sfx_killingblow x2, peppinoangryscream
	  L-> peppinoangryscream2	= peppinoangryscream2
	  L-> pepwakeup			= Voice-20
	  L-> pig			= [MI(PigOink1, 2, 3)]
	  L-> pigphoto			= pigphoto
	  L-> pizzagranny		= [MI(PizzaGranny1, 2, 3)]
	  L-> pizzahead			= [MI(Pizzahead1, 3)]
	  L-> sliderscream		= Scream
	  L-> swap			= [MI(Voice-13, 20, 21)], [MI(Noise2, 3, 5, 6)], [MI(Voice-04, 05, 06, 07, 08, 09)]
	  L-> transfo			= [MI(Voice-23, 22, 14)], Noise4
	  L-> vigiangry			= vigi2
	  L-> vigiduel			= vigi3
	  L-> vigiintro			= vigi1
	  L-> woag			= Noise2
	  L-> yodeling			= BrickYodeling
	\weenie
	  L-> bump			= WEENIE_BOING
	  L-> start			= sfx_weenieride

This took ALL DAY TO FINISH!!!

--------------------------------------------------------------------------------------------------------------

Made by burnedpopcorn180 on Github

<--- The Guide was meant for the Noise Update, but could also apply for older versions --->


```
