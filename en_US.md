# ResourcePack Server

A mod that allows you to host a resource pack server on your own server.  
(This mod has been downloaded 355 times as of 2024/02/16.)  

## Motivation

In the video game Minecraft, a resource pack can be used to alter the game's textures, sounds, music, language files, end credits, splashes, and fonts.  
It provides a simple means to customize the game's appearance and introduce new features.  
Many servers utilize resource packs to enhance the gaming experience for players.  
However, vanilla Minecraft servers do not support hosting resource packs natively.  
Instead, you typically have to host the resource pack on a third-party website, which can be inconvenient for players and server moderators, especially for developers who frequently update the resource pack.  
This mod aims to address this issue by enabling you to host the resource pack directly on your own server and easily share it with players.

## Plan and Progress

### Part 1: Preparations Before Mod Development

- [x] Learn how to create a mod for Minecraft
    - [x] Acquire proficiency in Java and Kotlin
        - [x] The basic syntax of Java and Kotlin
        - [x] Understand how to utilize Java reflection in Kotlin
    - [x] Familiarize yourself with using the Fabric API to develop mods
    - [x] Learn how to utilize Fabric networking to send and receive packets
    - [x] Understand how to use Fabric commands to introduce new commands to the game
    - [x] Learn how to use Fabric mixins to modify the game's behavior
        - [x] Learn how to utilize IntelliJ IDEA to decompile the game's source code

### Part 2: Mod Development

- [x] Develop a configuration manager to handle the resource pack server's configuration  
      (This necessitates the use of Java reflection)
- [x] Determine how servers send the resource pack download request to clients
- [x] Develop the resource pack server manager
    - [x] Implement functionality to start and stop the resource pack server
    - [x] Enable the ability to change the resource pack
    - [x] Calculate the SHA1 hash of the resource pack
    - [x] Send the request to clients

## Solved problems

### [Server not prompting client to download](https://github.com/iceice666/resourcepack-server/issues/3) 

#### Description

The sha1 value does not update after update the resourcepack.

#### [Solution](https://github.com/iceice666/resourcepack-server/pull/4/commits/91e0ff98ac171994bc61f9500f04c04ce6767dfc)  

The injected class is only called once when the server starts up.  
As a result, when we update the resource pack, the SHA1 value does not get updated.  
The solution is to inject into the class responsible for making a **resource pack download request**.  
This way, each time the server sends a resource pack download request, the correct SHA1 value will be sent to the client.


## The thing what I learned

This mod is hosted on GitHub, so when people encounter problems or bugs, they report them in GitHub issues.  
In interacting with them, if they provide incomplete information, it's necessary to guess or guide them step by step to fully describe the situation.  
Sometimes, there's no response for half a month.  
At that time, I feel tired and wonder if I should just ignore them.  
However, resolving the issue and seeing it closed makes me feel relieved.


## References and Resources

- [Minecraft Wiki - Resource Pack](https://minecraft.gamepedia.com/Resource_pack)
- https://fabricmc.net/wiki/start
- https://fabricmc.net/wiki/tutorial:networking
- https://fabricmc.net/wiki/tutorial:commands
- https://www.runoob.com/kotlin/kotlin-tutorial.html
- https://www.runoob.com/kotlin/kotlin-basic-types.html
- https://www.runoob.com/kotlin/kotlin-extensions.html
- https://www.runoob.com/kotlin/kotlin-extend.html
- https://www.runoob.com/kotlin/kotlin-data-sealed-classes.html
- https://www.runoob.com/kotlin/kotlin-class-object.html
- https://juejin.cn/post/6844903829868134407
- http://amitmason.blogspot.com/2018/08/kotlin-annotation.html
- https://medium.com/@eric61011/kotlin-%E7%AC%AC9%E8%AA%B2-%E4%BB%8B%E9%9D%A2-interface-b659954d05e8
