# Runescape-Web-Walker-Engine
##### Open-sourced world walker engine and path generation for Rune Scape written in Java.

## How to import to Tribot Scripts Folder
- Simply copy the webwalker_logic package inside your scripts directory! (View below) If you need further help, the visit the [Scripting Help Channel](https://discord.gg/T7QeCm3) on Tribot discord. 
- You can also clone this repo directly in your scripts directory with a few tweaks.

<p align="center">
  <img src="http://i.imgur.com/Age76Qx.png"/>
</p>

<p align="center">
  <img src="http://i.imgur.com/Fxvn5C1.png"/>
</p>

## Documentation
View [JavaDocs](https://itsdax.github.io/Runescape-Web-Walker-Engine/)

## API Keys

The public key is limited to a combined total of 400 calls every minute. The public api key is already included in the source.

If your scripts have a large userbase, then the public key may not be enough for your needs. If you require more calls or wish to support my project, please refer to [this link](https://tribot.org/forums/topic/68923-universal-web-walker-open-source/) or contact me over Tribot for API Keys. 

## About
- This is the **front end** of my web walker, which includes a wrapper for the server-client interaction of generating paths from point A to point B and navigating through the path.
- Back-end pathfinding is coded using a combination of dijkstra's and A\* algorithm. Dijkstra's is mainly for region limiting for performance purposes whereas A\* calculates the actual path. Wayports (Node jumps) cannot be calculated using a heuristic value so Dijkstra's is needed in this scenario.
- The Walker Engine includes path walking, waypoint navigation (Ship Chartering/Portals/etc), and path randomization using BFS to prevent trackable walking patterns.


## Features
- Speed. Will generate a path from any two points (Given that it is mapped) in less than a second, guaranteed.

- Simplicity. Implement the engine into your script by simply calling:
```
      WebWalker.walkTo(new RSTile(x, y, z));
      WebWalker.walkTo(new RSTile(x, y, z), walkingCondition);
      WebWalker.walkToBank();
```

- Shortcuts. Using all and only the shortcuts that your Player can access, whether it is skill level (Agility level needed for shortcut) or inventory item requirements (Such as gold needed for ship or fee to enter dungeon). This also includes quest requirements.

- Obstacles. All obstacles such as doors/ladders/etc are supported as long as area is mapped.

## Supported Areas (Currently roughly 90% of the game world)
- All Cities (Except Lletya) including Zeah
- Wilderness
- Gnome Slayer Dungeon
- Relleka Slayer Dungeon
- Stronghold of Security
- Most underground locations (Falador Mine, Varrock Sewers, etc)


## Debug
- Debugging visualization. Draw a live feed of the **Path** and **Collision Data** the engine is working with on the minimap using:
      ```
      WebWalkerPaint.getInstance().drawDebug(graphics);
      ```
      
<p align="center">
  <img src="http://i.imgur.com/17hx5iK.png"/>
</p>

<p align="center">
  <img src="http://i.imgur.com/gLMRq0O.png"/>
</p>

## Directed Nodes
- Nodes that direct to another, and not vice versa (Such as one way entrances) are supported as well.

###### Here is an example of Draynor Manor's one way door

<p align="center">Path from outside to inside. (Enters front door.)
<p align="center">
      <img src="http://i.imgur.com/2B2MyZ8.png"/>
</p>

<p align="center">Path from inside to outside. (Exits through back door.)
<p align="center">
<img src="http://i.imgur.com/Ne2Ydy1.png"/>
</p>

## What's Included
- Client side shortest path calculation for every location in the current region in a single call.

###### Real time visualization:

  ```java8
  Reachable.getMap();
  ```
<p align="center">
  <img src="https://i.imgur.com/4hZi3eM.gif"/>
</p>

## Visualization of the server generating a path from point A to point B (Slowed Down)
The algorithm is designed to limit itself to only the regions that will lead towards the destination. This is how we will generate paths in the fastest time possible.
###### UI is coded on a canvas in JavaFX. Code is not included in this repository.

<p align="center">
  <img src="http://i.imgur.com/ZD7hKWZ.gif"/>
</p>
