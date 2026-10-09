# 2copyOrNot2copy
open source script to check versions of scripts and assets (chunks) in a project and copies just what's necessary to update instead of updating the whole thing as a single package

With this script, I intend to put out there available to all something to help avoid infinite >3GB downloads (yes, I have a 20MB/s max download speed) for programs (but I thought mainly about games) that have added some very little new stuff <1GB but need you to download the full >3GB program for it to be updated.

Mainly, I thought about what thing games like War Thunder and Destiny 2 did wrong, and how could World of Tanks be so much better in their updating pipelines.
This is what I thought of:
  War Thunder and Destiny 2 are huge packages that cannot be separated from other dependencies and most of anything is just a jumble of connections, with just one or two places where there are very clear interfaces or internal APIs, while WOT have their code divided enough that they just need to download all their updated stuff in 1 or 2 GB and they just need to replace each necessary microservice with the updated version.

So this is a python implementation of exactly that idea.

For the idea to work, the project must be clearly divided in chunks or microservices, where each microservice has clearly defined limits.
There are four types of elements: the index, the interfaces, the microservices and other assets.
All elements that are not the index, have an ID belonging to them and only to them, and this ID has two parts: an element identifier and a version number.
The index will have inside all the available IDs.

So the functioning pipeline would be something like: 
- Start the updater: check with the remote version in the main server to see if there are any higher versions of elements and/or new elements than those in the local index
  - if there are bigger versions, download and/or change just the updated modules, and leave the rest alone untouched.

Basically, this is how pip and git work at a high level, but the companies with those games mentioned don't seem to value the cost in time (downloading the updates) and memory occupation (because usually unupdated_game + update_of_full_game >= unupdated_game * 2) they inflict on their players.

Of course, this needs a proper previous planification of the chunking the architecture of the game, where to put interfaces and what element has access to what other interfaces, but the potential gains are very big, even in development times, especially nowadays with AI vibe coding, where you usually can't compare your old versions with the new versions.
