# Customizing Your Nutscript Server

## Overview
In the last tutorial, you learned how to purchase a server, install Nutscript, and install a custom schema.  
Now, we will customize the schema, using the base as a template.

## Factions
One of the most important sections in the custom schema are **Factions**.  
More commonly known as teams, these allow you to split up players based on what their characters do.  
They can also be used to create Staff positions for administration purposes.

### Setting up Factions
1. Navigate to the schema folder
2. As shown below, you will see that there are already 3 sample factions provided: sh_citizen.lua, sh_law.lua, and sh_politic.lua
![image](/faction_examples.png)
3. To start with, let's open sh_law.lua. The code will look something like this.  
![image](/sh_law.png)
4. Here, you can change the name, salary, model, and many other variables.  
You can create as many factions as you want, and base them off of the samples provided.

## Items
**Items** are another schema cornerstone. These include anything that players interact with, including weapons, clothes, and medkits.  
Like with factions, the sample schema already provides a solid list of items to start with.  
Since these vary greatly depending on the gamemode, there is not one single item that will work for everything.  
However, there are many public GitHub repositories that give an idea on how to start with each type of item.  
You can create as many items as you like, and assign them to factions, as well as VIP roles using **flags**.

## Flags
**Flags** give and remove user permissions. By default, there are a list of flags that Nutscript comes with, including vehicle flags, physgun flags, and others. These can be found in-game, and are easily modifiable.

### Creating Custom Flags
In addition, you may want to create flags of your own. This is especially useful when creating VIP roles, as you can restrict certain items or factions to people who have that role.
1. Navigate to **gamemodes/yourschema/plugins**.
2. Create a new file with the name of your flag (ex: myflag.lua)
3. Follow this format, replacing the middle section with your code.  
![image](/flagsample.png)

