AardwolfMudlet is an Aardwolf package for Mudlet client created specifically for Aardmud. Mudlet is A cross-platform, open source, and super fast MUD client with scripting in Lua.

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/aardwolfmudlet.png)

Installation
===========

open mudlet, connect to aardwolf.

extract this zip to your mudlet profile directory: https://github.com/xekon/AardwolfMudlet/archive/master.zip

on linux:

    /home/kazuma/.config/mudlet/profiles/Aardwolf/aardwolf/aardwolf.xml

on windows:

    C:\Users\kazuma\.config\mudlet\profiles\Aardwolf\aardwolf\aardwolf.xml

From menu, choose Toolbox -> Module Manager -> Install -> select the aardwolf.xml file you extracted, have the sync checkbox selected.

Now close and relaunch Mudlet Twice!

in the mapper resize the rooms to size 10

drag the GUI elements around to resize it the way you want (RIGHT MOUSE BUTTON!), then type guisave

you may also notice the command separator does not work as you may expect, by default it is configured as ;; you can change it to a single semicolon ; in the options, goto options > preferences > input line.


Notes
=====

Most of this code is in a disorganized Prototyping/pre Alpha stage. Most things function but there's still a lot of work left. I am releasing this early because I have had a lot of requests from Linux/mac users that want to play aardwolf on a client without having to bother with using Wine to run Mush. This is also the reason I began working on this package, I am a linux user, and secondly I enjoy coding, I find it to be a TON of fun!

I began working on this while being a caregiver for my father, he has now passed on. I am needing to dedicate my time to earning a living to support my family. I am still VERY interested in working on this, and may contribute here and there, but certainly nowhere near the amount of time I had been. Please send pull requests or even FORK this if that works better for you. I will eventually come back to working on this more often, but I suspect it will be a year before I have the time.

I have included a base starter map with aylor and continents similar to how Mush does. If you have 96% explored or more (rank 15) then I would be happy to share my complete map file with you to save you most of the remapping work associated with changing from one Mud client to another, just send me a message or leave a note in game (my character is Kazuma).

AardMush makes use of many tags that my script does not currently use, AardMush automatically turns these tags on, so if your jumping back and forth between clients you will see this as extra output on the screen. When using Mudlet you can send this string of commands:

    tags bigmap off;tags coords off;tags mapexits off;tags mapnames off;tags roomdescs off


Features
=====

clickable links for quests/gquests (similar functionality to Search and Destroy, but interface needs its own window and a bit of streamlining.)

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/quest.png)

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/campaign.png)

Automapper Window (the small ASCII map)

Gmcp mapper code to track and build mapper database.

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/mapper.gif)

Group Interface Window with damage meters. ("damage 0" is the only mode currently tested.)

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/epic.png)

Tabbed chat interface.

parts of the interface can be dragged and dropped in different predefined areas. To drag and drop item or resize the frame you right click on the tab or the blue drag handles and drag the mouse.

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/move.gif)

Currently script config is handled by typing "vc" or "vconfig" these values are saved PER Character, so if you enter aardwolf with a different character/alt it will automatically store these to a seperate config file based on your character's name.

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/vc.png)

Gquest/war sound notification when its within your level range.

runto alias, this alias is used from recall and adds the ability to runto.

rf room_name_keyword search the mapper for part of a roomname and provide clickable link to run to it.

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/rf.png)

rfa room_name_keyword search the mapper within the current area for part of a roomname and provide clickable link to run to it.

typing "where" or "where mob/player" provides clickable links to get to that player or mob.

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/where.png)

guisave - type to save the gui layout.

campaign leveling - automatic noexp toggle, customizeable exp threshold

Note to disable this feature: vconfig cpexp -1

there is a flyout clanshop speedwalk menu in the topleft corner.

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/shops.png)

chat channel/event sounds

when using the cardinal direction keys, the presence of a door is checked and issued if exists.

pup stat reporter, currently if the groupsize is greater than 5 then it does not fire, this was to prevent me from accidentally having it enabled in EPIC runs.

Player notes, type "finger <player>" and you will see a clickable link to add a note about that player.
    
potion count tracking(some bugs to work out, just haven't had time, such as two different types of potions, and count of last seen type is used.)

consider all, color coordinated level difference shown.

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/ss1.png)

![AardwolfMudlet](https://raw.githubusercontent.com/xekon/AardwolfMudlet/master/ss/ss2.png)

F4 key shows count of rooms in area for the mapper and also sends "explored" this allows you to compare how much of it you have mapped vs explored.

Shift+F4 key does same as F4 but it also prints a list of rooms with their Vnums for the Area you are currently in.

F8 key is used to map area portal command that does not use the "enter" keyword for example "enter red", for example if the portal command was instead "sit carriage"

Todo List
=====

Vidblain speedwalks work when performed from recall using runto (there is an alias for this) It works by waiting until you enter vidblain and then completing the rest of the speedwalk. The part of this that does NOT work is when the speedwalk is performed using mapper functions such as "lua gotoRoom(19643)" These are the functions that are used with the clickable links for quests/campaigns. I believe the easiest way to correct this is to modify the buildSpeedWalk() function that I wrote, so that certain keywords or parameters such as "vidblain" are processed differently by the speedwalk function, this way certain keywords could be used in the custom exits field of the mapper and processed properly, instead of just being sent to the mud.

Also the triggers used for clickable links for quests/campaigns need to be adjusted to work with gquests as well (easy)

S&D has basically a shortcut/portal aware runto with "xrt <area>" some of the code I used for campaigns basically does this, it just needs to be incorporated into an alias and debugged for any gotchas.

The mapper code does not work as flawlessly as it does in Mush. If you have ever used zmud/cmud, you will remember how sometimes things need re-positioned or even deleted and recreated, these are the type of issues you will have until the Mudlet mapper code for aardwolf is improved further.

The flip-side of the mapper in Mudlet vs AardMush, is that you can position rooms, etc in a way that is comfortable for you! I myself move all rooms to the 0 axis, so that all rooms are visually on the same level, giving the mapper a similar view to the image maps available on many clan websites. Also for the most part you only have to map an area once, and then its Done, and you can use it!

currently there is a lookup index for areas in the scripts labeled "areaIndex" this serves the purpose of converting from the areas full name to the gmcp data area shortname. This allows the areaname to be looked up for the clickable links for quests/campaigns. Something to be aware of is that if a new Area is added to Aardwolf it will need to be added to this script as well.

Nomaps rooms are not currently mappable, these are rooms that return a vnum of -1, as can be seen by going to a nomap room and doing this: lua display(gmcp.room.info) It is actually possible with Mudlet to map these rooms based on roomname and last used direction, which is how zmud did it. Obviously the issue with this is that true mazes will not map correctly because the rooms/exits move/change. However for rooms like the entrance to Living Mines of Dak'Tai, these type of rooms should be fully mappable once some additional code is written. I had planned to also write a toggle for mapping for the mode mapping/follow similar to how zmud had. When in follow mode it would NOT map nomap rooms, this is to prevent creating a mess of new rooms in your mapper when navigating a maze.

The damage meters portion of the group interface was something I added after creating the initial group frames, some of the code for this is in captures/gags/epics/damage. This needs to probably be moved, a config should also be added for the gagging of the damage, currently if the group is 5 or more then the damage is gagged (spammy EPIC assumed.)

Area Portals - I have not worked out implementing these yet, there is a post by Vadi (Mudlet developer) in forums that links to an example script of how to accomplish this: https://forums.mudlet.org/viewtopic.php?p=24346#p24346

Some of the features I have implemented need a toggle on/off config variable set and added to the config "vc" I am sure some of the features I use other people may want to have the ability to disable.

Currently if you add an additional window to the guiLoad() function, and then save it as part of your layout by using "guisave" if you later comment out or remove that additional window GUIFrame bugs out with nil window, which break the load event. to fix this just load mudlet with the extra window removed, then type "guisave" then relaunch. I planned to add this bug fix to the GUIFrame framework latter. (nil window handling)


In progress code
=====

INFO data tracker, track the various data messages on INFO channel. I completed some of this, the data for levels, deaths, pups are all tracked, you can view the data by typing "lua display(aard.adt)" I planned to create a window to display this data in a pretty way, the window was only going to show on mouseover or click of a button at the top, probably above the mapper. I also planned to track other things as well eventually, like gold/minute/area etc.

an inventory management scrip with database backend (think dINV) but with clickable UI similar to the basic config I implemented. "vc" The idea was to have something similar to dINV but have as many things be clickable links as possible, to make it simpler to use. For example, if you bid on an item on the auction, embed a clickable link in that output that automatically print a table of comparable equipment (dINV covet) What I dislike about dINV is that there is a lot to learn to use it efficiently, to the creators credit the helpfiles are excellent, but when possible I like scripts to be very accessible without even having read the help files. Most of the Triggers for this are finished in the folder labeled itemDB, also key F7 is an example of how to create a simple sqlite3 database. This is the project I was currently working on, I just don't have the time.


Planned extra features
=====

a Partroxis helper for Mudlet: https://github.com/galaban/partroxis (Mush)

Use the same sound package for events that AardMush uses (its what's familiar for most users.) The sounds that my package uses are the ones I have used for years, so its what I myself am comfortable/familiar with, I used them since way back when i used zMud.

I had planned to contribute to Mudlet making it easier to tell how directions are linked instead of a straight line from one room to another, tracked here: https://github.com/Mudlet/Mudlet/issues/2427


Credits
=====

The very helpful people on the Mudlet Discord! (Vadi, SlySven, Eraene, and many others.)

https://github.com/daagar/damp (great example of how to work with the mudlet mapper using gmcp)

https://github.com/fiendish/aardwolfclientpackage (Aardwolf MUSHclient by Fiendish)

https://forums.mudlet.org/viewtopic.php?p=44735 (GUIFrame by Jor'mox)

https://wiki.mudlet.org/w/IRE_mapping_script (IRE scripts by Vadi)
