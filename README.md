# Curseforge to MultiMC importer

A windows script to import instances from Curseforge to MultiMC launcher.

## How this works

Both Curseforge and MultiMC have a similar but slightly different instance folder structure. The difference is that the instance folder of the Curseforge client represent the .minecraft folder in the MultiMC instance. To make the Curseforge instance work with MultiMC the necessary steps to take are the following:
1. Create a folder with the same name than the Curseforge instance at <code>${MulciMC}\\instances</code>. In following will work with the example folder "<code>Modpack</code>".
2. In the folder <code>Modpack</code> create a windows folder-link to the respective instance folder the Curseforge (here: <code>${Curseforge}\\minecraft\\instances\\Modpack</code>). The *command line* (!NOT POWERSHELL!) command   
<code>mklink /J ${MultiMC}\instances\Modpack\.minecraft ${Curseforge}\minecraft\Modpack</code>  
will create the desired outcome.
3. After creating the link we need to tell MultiMC that there is a minecraft instance located in the newly created folder (<code>${MulciMC}\\instances\Modpack</code>). We also need to tell MultiMC that this minecraft version uses forge - a specific version at that - to load mods.  
This is done in 2 files: 
  - <code>${MulciMC}\\instances\Modpack\instance.cfg</code>  
    This file is the configuration of MultiMC for this specific instance. An example version could look like [this](./examples/instance.cfg). 
  - <code>${MulciMC}\\instances\Modpack\mmc-pack.json</code>  
    This file states the version of minecraft itself, forge and additional libraries that are used, in most of the MultiMC instances there will be a version of [LWJGL](https://www.lwjgl.org/), too. [This](./examples/mmc-pack.json) is an example of the file.