# Custom Planet Descriptions in Starsector

Before starting the procedure, please backup your save.

You will need the Console Commands mod.

First make a mini starsector mod. In your starsector folder go to mods and make a folder, name it whatever you want. Go to the folder and make a folder named `data`, then go to data folder and make a folder named `strings`. In the `strings` folder create a file named `descriptions.csv`.

Open `descriptions.csv` with any text editor (Notepad will work). Copy paste this:
```csv
id,type,text1,text2,text3,text4,notes
id,CUSTOM,"text",,,,
```

Now, replace `id` with any name (underscores only). Say you just invaded `Jangala`, now you want to update the description to reflect the recent invasion. So, `jangala_invaded_desc` might be a good ID, and the text can be something like `"Until recently, Jangala was the territory of the Hegemony. Now, it is a planet owned by the glorious FACTION_NAME"`. Replace `FACTION_NAME` with your faction and **do not remove the quotemarks**.

Save this file.

Now, your "mod" needs to be recognized by Starsector for your new description to apply. Create a file named `mod_info.json` and put this in it:
```json
{
    "id": "my-priv-modifications",
    "name": "My Private Modifications",
    "author": "YOUR_NAME",
    "utility": true,
    "version": "0.1.0",
    "description": "My private modifications for Starsector, such as planet descriptions my colonies",
    "gameVersion": "0.95.1a-RC6"
}
```

Replace `YOUR_NAME` with your name.


Go to the system containing the place whose description you want to change. 
Now, in the console (open with CTRL+Backspace), find the ID of the colony whose description you want to modify with `list planets` and `list stations`. Get the ID of the colony (e.g `jangala`).

Now, to alter Jangala's description to reflect your invasion of it, run this code:
```java
SectorEntityToken entityToRename = Global.getSector().getPlayerFleet().getContainingLocation().getEntityById("jangala"); entityToRename.setCustomDescriptionId("jangala_invaded_desc");
```

Exit and save your game, exit Starsector and relaunch. Upon relaunch, activate your private mod containing the description. Then, launch Starsector and when your game loads, you'll find that your planet now has a new description!

# Giving your save to others
If you decide to give your save to others, send them the "minimod" with the descriptions. Even without the minimod, the save will still work but the descriptions will just read `No description... yet.`.

# Copyright
This document has been placed into the public domain by its author, Lemuria#0685. In simple terms, this document has no copyright.

<sup>Authorized by the: *Luria Federation - Office of the Colony Database*, August 10, 2022</sup>

