# Creating a Garry's Mod Server with the Nutscript framework

## Overview
**Nutscript** is a framework for creating Garry's Mod servers, focused on serious gameplay.   
This tutorial will guide you through setting up your server, installing Nutscript and a sample schema, and give some customization options.

---

## Purchasing a Server
1. To begin, you should purchase a server from any reputable server hosting company (Nodecraft, Apollo, Physgun, etc.).  
2. Choose a player count - 32 is generally acceptable to start with, and you can upgrade to 64 or even 128 players if your server gets popular enough. 
3. Purchase a server configuration of your choosing, create an account, and log in.
43. Once logged in, you will have access to 4 important pages - the **Panel**, the **Config Editor** and **Startup Settings**.

### Panel
The Panel is the most important part of your server, as it acts as a directory for all of the files that you will be using.
A sample is shown below.
![image](/panel.png)

### Config Editor# Creating a Garry's Mod Server with the Nutscript framework
The Config Editor provides a variety of modifiable values, mainly centered around the base traits and security of your server.  
Here, you can set your **Hostname**, **Password**, **Loading URL** (what image players see when loading in to your server), and other variables.
![image](/config.png)

### Startup Settings
Startup Settings allow you to modify important variables like the map, workshop ID, and gamemode.
![image](/settings.png)

## Installing Nutscript and a Sample Schema
Setup consists of two parts - installing the **Nutscript** base gamemode, and installing a custom **schema**.   
A **schema** is a custom gamemode that runs on top of the base Nutscript gamemode, allowing you to customize the environment to your liking.

### Installing Nutscript
1. Head over to https://github.com/NutScript/NutScript and download the latest version of Nutscript.
2. Open your server panel directory.
3. Drag and drop the installed folder into your **gamemodes** folder and rename it to **nutscript**.

### Installing a Schema
Although you can eventually create your own schema, it is recommended when starting out to use an already created one.  
One popular choice is **ModernRP**, which will be used in this tutorial.
1. Navigate to https://github.com/rebel1324/modernrp and download the latest version.
2. Drag and drop the installed folder into the **gamemodes** directory as before, and name it what you would like your gamemode to be called.

Now you are ready to customize your schema!

# Customizing Your Nutscript Server

## Overview
Now that the server is setup, we can customize the schema, using the base installed earlier as a template.  

## Factions
One of the most important sections in the custom schema are **Factions**.  
More commonly known as teams, these allow you to split up players based on what their characters do.  
They can also be used to create Staff positions for administration purposes.

### Setting up Factions
1. Navigate to the schema folder
2. As shown below, you will see that there are already 3 sample factions provided: sh_citizen.lua, sh_law.lua, and sh_politic.lua
![image](/faction_examples.png)
3. To start with, let's open sh_law.lua. The code will look something like this.  

```lua
FACTION.name = "Law Enforcers"
FACTION.desc = "The people who enforces the laws of the land."
FACTION.color = Color(70, 70, 255)
FACTION.isDefault = false
FACTION.isPublic = true
FACTION.salary = 300

-- http://steamcommunity.com/sharedfiles/filedetails/?id=170149842
-- NYPD Male Models
-- New Model's default anim set is "citizen_male". No need to setup new animset.
FACTION.models = {
	"models/nypd/male_02.mdl",
}

FACTION_LAW = FACTION.index
```  



4. Here, you can change the name, salary, model, and many other variables.  
You can create as many factions as you want, and base them off of the samples provided.

## Items
**Items** are another schema cornerstone. These include anything that players interact with, including weapons, clothes, and medkits.  
Like with factions, the sample schema already provides a solid list of items to start with.

1. To create a custom item, navigate to **schema/items** and create a new file with the name of your item in this format: **sh_item.lua**
2. Make sure you generally follow the format below.

```lua
ITEM.name = "Spade" 
ITEM.desc = "A multi-purpose shovel"
ITEM.model = "models/weapons/tfa_nmrih/w_me_spade.mdl"
ITEM.class = "tfa_nmrih_spade"
ITEM.weaponCategory = "melee"
ITEM.width = 3
ITEM.height = 1
ITEM.price = 0
ITEM.iconCam = {
    pos = Vector(-12, 189.54248046875, 3),
    ang = Angle(0, 270, 0),
    fov = 15.882352941176
}
ITEM.flag = "y"
```

To get the model, you will use the file name of the item that you are using.  
At the bottom, you may include a custom **flag**, which allows you to restrict the item to certain groups who have it.

## Flags
**Flags** give and remove user permissions. By default, there are a list of flags that Nutscript comes with, including vehicle flags, physgun flags, and others. These can be found in-game, and are easily modifiable.

### Creating Custom Flags
In addition, you may want to create flags of your own. This is especially useful when creating VIP roles, as you can restrict certain items or factions to people who have that role.
1. Navigate to **gamemodes/yourschema/plugins**.
2. Create a new file with the name of your flag (ex: myflag.lua)
3. Follow this format, replacing the middle section with your code.  

```lua
local PLUGIN = PLUGIN

PLUGIN.name = "PAC3 Flag"
PLUGIN.author = "Luna"
PLUGIN.desc = "Adds a flag to PAC3."

do

function PLUGIN:PrePACConfigApply(client)
	return client:getChar():hasFlags("3")
end

function PLUGIN:PrePACEditorOpen(client)
    return client:getChar():hasFlags("3")
end

end

nut.flag.add("3", "Access to PAC3.")
```

At the bottom, you can choose the name of the flag, which can be any letter or number, as long as it isn't already taken.  

## Conclusion
In this tutorial, we learned how to purchase a Garry's Mod server, familiarized ourselves with the server hosting sections, downloaded Nutscript and a custom schema, and learned the basics of customization.

With these skills, you can now start delving deeper into the design of the server, remembering the foundations that are critical to any new Garry's Mod server project.
