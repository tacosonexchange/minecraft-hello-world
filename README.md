### 📰 Overview
Creating add-ons for Minecraft: Bedrock Edition (henceforth referred to as simply BE) is a relatively straightforward process that, more often than not, requires little to no knowledge of programming. Getting started, you'll need to have an understanding of some basic terminology:

Term | General Definition
---- | ------------------
Resource Pack | *A partial add-on for Minecraft that enables creators to alter the **appearance** of the Minecraft worlds that implement them.*
Behavior pack | *A partial add-on for Minecraft (specifc to BE) that enables creators to alter the **behavior** of the items and entities used in the Minecraft worlds that implement them.*
JSON | ***JavaScript Object Notation** is a lightweight format for storing and transporting data that is often used when data is sent from a server to a web page. It is "self-describing" and easy to understand.*
UUID | *A universally unique identifier (**UUID**) is a 128-bit label used for information in computer systems. The term globally unique identifier (**GUID**) is also used, often in software created by Microsoft. When generated according to the standard methods, UUIDs are, for practical purposes, unique.*
.mcpack | *The file extension used for individual resource or behavior **packs**. This is used in a one or the other situation.*
.mcaddon | *The file extension used for **add-ons**. This is used when there is a resource ***and*** behavior pack included in a single package.*

### 🏅 Objectives

After reading this answer through and through, you should be able to effectively answer the following questions:

 - What is an add-on?
     - What is a resource pack?
     - What is a behavior pack?
     - What is the difference between the two?
 - What does `JSON` stand for?
     - What is `JSON` used for?
 - What tools are required to create an add-on?
 - What official resources are available for creating add-ons?
 - What official documentation is available for reference when creating add-ons?

### 🔨 Required Tools
The only tools ***required*** for creating an add-on for BE are text editors. Some of the most popular OS agnostic text editors are:

 - [Visual Studio Code][1]
 - [Atom][2]
 - [Sublime Text][3]

Alternatively, [here is an article][4] reviewing a list of 10 text editors that are OS agnostic.

### 📝 Getting Started
Once you've chosen and installed the text editor of your choice, the first thing you'll want to do is download [the vanilla packs][5]. The vanilla packs are going to be a point of reference for anything and everything (excluding scripts) that you may want to accomplish with your custom add-on. It is also recommended that you watch [the official introduction to add-ons][6] video.

Once you've downloaded the vanilla packs, feel free to explore their contents and get familiar with the structure:

[![Screenshot of the folder structure and an open manifest file in Visual Studio Code.][7]][7]

<sub>***Note**: I'm using Visual Studio Code in the screenshot above, but you can browse the folder structure in the file explorer or text editor of your choosing.*</sub>

### 👋 Hello Minecraft
Now that you've familiarized yourself with the content structure of the vanilla packs, you're ready to start getting your feet wet by creating your very first add-on. The basic requirements of an add-on are:

 - A resource ***or*** behavior pack.
     - A manifest file describing that pack.

You're probably wondering, "is that it?!", well, yeah, it is. Your add-on doesn't actually require a behavior pack ***and*** a resource pack. In-fact, only one ***or*** the other is required, though both can be included. For the purposes of this answer, the resulting add-on will include both.

To get started, create a folder with the name of your add-on (I called mine ***Hello Minecraft***) and then two folders within that one called ***Behavior Pack*** and ***Resource Pack*** respectively (henceforth referred to jointly as the pack folders). Within the newly created pack folders, create a file named `manifest` with a file extension of `.json`. The resulting stucture should look like this:

[![Screenshot of the basic file structure in Visual Studio Code.][8]][8]

The manifest file is different for behavior packs and resource packs. However, you can grab a sample of both from the vanilla packs to populate the files you just created. Next, you'll need to generate ***four*** UUIDs two for each pack. Both packs have a header UUID and a module UUID:

    {
        "format_version": 2,
        "header": {
            "description": "An example resource pack for demonstration purposes.",
            "name": "Hello Minecraft! - Resources (0.0.1)",
            "uuid": "efcd2de9-44b2-4201-ba94-6b82ef59de0f",
            "version": [0, 0, 1],
            "min_engine_version": [ 1, 17, 0 ]
        },
        "modules": [
            {
                "description": "An example resource pack for demonstration purposes.",
                "type": "resources",
                "uuid": "fca45bed-c308-42ad-9b54-690083e7dc3e",
                "version": [0, 0, 1]
            }
        ]
    }

The manifest file has an additional field available labeled `dependencies` which you'll see in the vanilla behavior pack manifest:

    "dependencies": [
        {
            "uuid": "efcd2de9-44b2-4201-ba94-6b82ef59de0f",
            "version": [0, 0, 1]
        }
    ]

The UUID in this section is set to the header UUID of the respective dependency. So in the case of this add-on, the behavior pack will be dependent on the resource pack. As a result, the dependency UUID is the header UUID of the resource pack.

### 🧱 Bundling and Importing
Once you've set your UUIDs, you can then bundle your add-on and import it into Minecraft! To do this, you can store the folders relevant to your add-on (in this case the pack folders) in a single archive file (commonly referred to as `.zip` files, but this can vary based on OS). After you've placed your add-on contents into an archive file, you can change the file's extension to `.mcaddon` which will allow you to open the add-on with Minecraft. Importing is as simple as opening the file with Minecraft, from there the process is automated.

Once imported, you should see your packs in Minecraft:

[![Screenshot of the resource pack after a successful import into Minecraft for Windows 10.][9]][9]

### 📑 Further Reading
Now that you've created your first custom add-on for Minecraft: Bedrock Edition, you may be curious as to what documentation is available to you. Fortunately, the vanilla packs include some basic, but official documentation within the behavior pack:

[![Screenshot of the documentation files within the behavior pack.][10]][10]

In addition to this, there are online resources (such as [Bedrock.dev][11]) that add styling to the aforementioned documentation, making it easier to follow, along with [official resources from Microsoft][12]. Also, [the fandom wiki][13] is a great resource to utilize when trying to [find data values][14] and really detailed information about Minecraft in general.


  [1]: https://code.visualstudio.com/
  [2]: https://atom.io/
  [3]: https://www.sublimetext.com/
  [4]: https://www.techradar.com/best/best-text-editors
  [5]: https://www.minecraft.net/en-us/addons
  [6]: https://www.youtube.com/watch?v=US67Tlb8gyE
  [7]: https://i.stack.imgur.com/siBOh.png
  [8]: https://i.stack.imgur.com/rpck3.png
  [9]: https://i.stack.imgur.com/tzCGw.png
  [10]: https://i.stack.imgur.com/oKSLh.png
  [11]: https://bedrock.dev/docs/1.17.0.0/1.17.20.23/Addons
  [12]: https://docs.microsoft.com/en-us/minecraft/creator/documents/gettingstarted
  [13]: https://minecraft.fandom.com/wiki/Minecraft_Wiki
  [14]: https://minecraft.fandom.com/wiki/Bedrock_Edition_data_values
