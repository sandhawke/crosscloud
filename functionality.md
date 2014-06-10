These are elements of user functionality provided or intended to be provided by Crosscloud.   This is roughly in order of increasing difficulty, or the order in which we expect them to be implemented.

Each is presented as a brief "user story", usually about "Alice" and "Bob", two example users of Crosscloud applications.   Alice and Bob like to play chess online.

Each should also be explained in terms of microblogging, and maybe another app.

Also, for each we should say where it is on the spectrum from being conceptualized as a problem to being an accepted deployed standard.

## Social App with Personal Online Database (pod) Servers

Story: Alice and Bob can play chess online, with a nice WebApp UI, without their game data touching a server outside of the control of either of them, or running a server that knows anything about chess.

## Individual Access Control

Story: Alice and Bob don't want anyone else to see their chess game

## Group Access Control

Story: Alice and Bob are co-workers at a company.  They want only the people at the company to see their chess game.

etc.


## Property-Based Access Control

Story: Alice and Bob want their game to be visible to anyone who published their agreement to certain terms of service about how they'll handle the game data they receive.


## Switching Apps, Same Data Interface

Story: In the middle of a game, Alice wants to switch to using a different chess app.  This other app implements the same data interface (vocabulary + data shapes) as the first one.



## Switching Pods

Story: Alice was using her work pod for her games with her co-worker Bob, but now she realized this isn't a work activity, so she wants to remove all trace of te game from her work pod, using a home one instead, but she wants all the game state to remain intact.   In fact, she'd like to do this in the middle of a game which several people are watching.


## Social Search (Same Data Interface)

Story: Alice wants to find someone to play chess with, right now, online.  He runs a chess app and which offers to search for people who want to play a game.   In this case, it only searches outward along her social network links.  If Bob is a friend, or a friend of a friend, and he's said he wants to play a game, it should list him to Alice as a possibility.

## Global Search (Same Data Interface)

Story: Like Social Search, but in this case it reaches people who are not in Alice's nearby social network.  They might not be in her network at all, or they might be so far away that they are among the billions of people at that distance.

Solution: namespace doc points to a tracker

## Data Location / Replication

Story: Alice and Bob are playing chess.  Alice's server goes off-line.  Can Bob still see the whole game?   Can Bob still see his moves?

## Nonreputiation

Story: Alice makes a microblog post, then later modifies her server so it shows it as having different text.   Bob should be able to detect this if he saw it before she changed it.

## Efficient Change Propagation

Story: Alice makes a move in her chess game with Bob.  Bob wants to see that move immediately. 

## Building on non-institutional data sources

Story: Alice is writing the first chess app and creates a vocabulary for it.  How does she document that vocabulary such that others are able and likely to reuse it?

## Switching Apps, Different Data Interface

Story: App1 uses vocab 1.  App2 uses vocab 2.  User wants to switch from App1 to App2 without losing access to data.

Solution: Include some rules in the namespace documents.   Link the input and output terms to the rules which use them.

## Search (Different DataIntf)

More difficult: Alice and Bob are using two different chess apps, which use different vocabularies.

## Trust

Use case: only pay attention to product reviews from people who are likely to be trustworthy, perhaps determined via my social network


## Bridging to Legacy Systems

(challenge, isn't this app code running on a server?  Or is this done via some specialized service you DONT control/install?)


## App Damage Control

Story: Alice runs App1 and App2 on the same data.  The data end up ruined.  Which one should she blame?   Can she get her data back?


## App Loyalty

Story: Alice wants to run an App on sensitive and important data.  How does she know the app wont leak or corrupt her data?

Solution: Benevolent Apps Certification


## App Privacy Leaks

Story: Alice wants to use a To-Do List app that has some interesting new features, but is not certified benevolent.  She does not want to trust the app not to leak her data.

Solution: Alice should run the app in a "cage" which prevents it from communicating except to pods she selects.   A cage is like a sandbox, but not only stops the app from hurting her machine, it also stops the app from communicating.  Caging could be implemented by a browser modification, or with Caja, a javascript embedding tool.

But it can still post to your pod, maybe where you wont notice, but it can see?  Maybe it's restricted to posting to some given interface?


## Outbound Scaling ("Justin Bieber" problem)

Use case: a microblog with millions of followers, hopefully without paying for thousands of servers


## Inbound Scaling

Use case: a query which needs to traverse thousands or millions of servers, for aggregation (star ratings), or for finding a few special bits.


