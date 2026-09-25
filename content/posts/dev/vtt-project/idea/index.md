+++
title="What is the VTT Project"
description=""
summary=""
date="2026-09-25T16:00:00+02:00"
categories=["any", "dev", "devlog", "vtt project"]
+++

For a few years already I have been wanting to do a VTT project. Nowadays there
are a few options around but they require either a one time payment that is not
possible for many countries and younger people or require a monthly fee that is
even more expensive.

I've been playing TTRPGs online for a long time and our tables always used
software not really built for this like Discord voip calls + a dice roll bot +
either chats on discord to share images or things like whimsical.com or
excalidraw.com to have a "table" with a grid for us to move our characters and
RP.

I also have been interested in descentralized tech for quite a while and wanted
to do something peer-to-peer. So I came with this idea.

## The idea

A peer-to-peer first 2D grid to play VTTRPG's as an alternative to things like
Foundry, Roll20 or Alchemy. It will be a native app for Linux, Mac and Windows,
tested only on Linux as I'm a single dev, so it will hopefully work on other
platforms.

The app will be shipped as a single binary that have both the client and the
server, the server is responsible to manage the data on the client and share it
with other peers.

### Brainstorm of features

> This is just a brainstorm of ideas, not features I necessarily plan on
> implement.

You can then create rooms or join rooms to play games, a room is a game
campaign, the GM is the room owner and admin, if it was not the GM that created
the room the perms can be transfered.

When you create a room libp2p will make so that you can make that room
available to your friends which will be other peers on the p2p network.

The app has a local db (turso) which save the state of the room and the server
is responsible for broadcasting over p2p the changes you made to the board and
receiving changes from the other peers.

Inside the room you will have a top down view of a canvas where players can edit
at the same time similar to Excalidraw, Miro or Figma.

This top down view at first will be a 2d canvas but in the future there might be
a 3d plane with the camera on top-down view where players would be able to 
import 3d models to it from blender.

On the 2d canvas player will be able to add images, change the size of the
images, move them around, draw above them, draw arrows, delete them, calculate
the distance between images based on a grid that will be in the canvas.

Players would be able set the image as Players, mobs, bg, etc. If its a player
or mob they can link it to a character sheet defininVR stereo rendering g the
stats and items it hold.

The canvas would save the state automatically at every change and you can revert
to any point in time similar to git and other distributed version control
software system. So there's a CRDT that auto-merge changes, but if it messed it
up users can chery-pick something different or revert to any point in the game.

Players would be able to roll dices, see previous rolls and there will also be
a small chat and history of rolls.

It there will be Plugin support, client side plugins where only one peer need to
have and server side or server/client plugins that all peers on that table need
the plugin to play (think alike how minecraft mods work), people should be able
to extend it by writting lua scripts or writing plugins in their favorite
language and converting it to wasm.

### Stack

> This is a simplified version, there will be more stuff like wasm and lua
> support if I do the plugins as stated before among other dependencies.

Client:

Go + Raylib-go

Server:

Go + go-libp2p + turso db (local), flatbuffers for communication


### MVP

- Player should be able to have a Whimsical/Excalidraw/Miro experience in a 
native linux app (can be compiled to Mac/Windows too, compilation should work,
will not be tested).
  - Add images
  - Add text
  - Images, text, etc are nodes that can be dragged around
    - nodes shold be able to be selected in groups
    - when a node is selected it sends a lock so that other players can view
    the node changes but cant edit the node
    - when a player lose connection or go offline the player can edit anything
    but when the player regain connection the player edits will be on a branch
    from the online server which then the player can request to merge some or
    all of it and the GM/admin can accept changes as they see fit (it automerges
    with CRDT and GM can change as needed).
  - See grid
    - Grid should have a helper to calculate distances
  - See changes in real time
  - see changes history
  - Revert changes in real time (GM)
- Player should be able to either connect to a P2P room or create one

- Automated interface tests and concurrency tests to make sure the app dont feel
buggy
- Work with players to validate that the interface is easy and simple to
understand and use


#### Future Features
- GM/Admin should be able to create character sheet templates for players and 
NPC's to use
    - Players can use the sheet templates to create their characters
- Interface should have a "Game directory" (name can change) in which all
images added to the game are there under an "assets" sub-directory but also GM
can add PDF's there such as the rulebook, character sheets, etc and can allow
players to modify some or all or them or make copies that they can modify
(permission system based on UNIX)
- Plugin system
- Dice rolling
- Personal space for notes to be added
- Chat for public notes to be added and coversations to be had

#### Interesting Ideas for the late future
- When focused on a player show a topdown shadow covering places where the
character cant see based on the vision range of the character and hide things
behind structures like walls
- Custom keyboard shortcuts to different actions that you might want to do
faster
- Way to integrate the rule book with your character sheet (hover skill and see
what it does type of thing)
    - Dont allow the player to add things on wrong spots of the sheet.
- OCR of PDF sheets to fast import

## My objective

The MVP features is the bare minimum I assume is needed to have a "table" which
is the most important part of a Table Top game. With the table done I will then
add the dices, sheets and file management so that you dont need to use external
dice rollers and so that GM's can import files for players such as the game
rulebook or old sheets in which the players can open on their PDF readers.

I will not add VoIP since that requires a centralized server, so the players
will need to figure out the platform they want to communicate with each other. I
will add a plugin system so that if any player want to add their own features
they can without need to have my approval to the project repo.

I will add the personal notes space since that's very important for TTRPGs and
probably a chat for text communication.

The idea is that all those systems are very simple to use and should work
flawlessly and not be hard to understand by the final user. The project should
perform as well as I can make it perform with the constraints of Go and P2P.

There might be a centralized version later where you can choose to self host in
case P2P is too slow or some of your players can't do Hole Punching, if the
project do well and I see people wanting it I could also provide a paid server
service hosted and maintained by me.

The idea is to be free and simple first, so that anyone from anywhere can play
VTTRPG's even if they're not experienced in it.

## Complexities of the project

Raylib is a CGO simple and opinionated game library that abstracts OpenGL with
rlgl, give you 2d and 3d support, shaders, math module, audio and texture 
loading, VR support, etc. Which will be used to draw the interface and
everything related to it.

While I have done interfaces for the web before with Vue, React, native JS and 
HTML + CSS, for mobile with Flutter and React Native, a small game with tkinter
and started a small TUI game where I built everything from scratch in Go I have
never worked with Raylib nor OpenGL.

LibP2P is a networking stack and library modularized out of The IPFS Project,
I have built a few REST and GraphQL API's but never worked with a descentralized 
network nor peer-to-peer.

Flatbuffers are a very cool cross platform serialization library that does not
need a parsing/unpacking step to a secondary representation before you can
access data, often coupled with per-object memory allocation and enables the
schema to evolve over time while still maintaining forwards and backwards
compatibility with old flatbuffers. I have mostly worked with JSON before, but
have had interest in flatbuffers for a long time and this seem the right project
to use it.

Turso is a new database that came from a rust rewrite of LibSQL a SQLite fork.
It provides some useful new things in comparison to SQLite such as Concurrent
Writes and Async Design.

I have heard of all the tech in the stack but I have never worked with any of
them, aside from the problems that I need to tackle (being CRDT Engine, Branch
Metadata, Event Store, P2P Sync, Conflict Detection, Concurrency, among other
things). Most of those I have never had to deal with or used abstractions to
solve it.

I'm very excited as no matter how far I go in it I will be learning a lot. I
will be posting in the blog updates on what I've been doing and the hurdles and
learnings I had during development.
