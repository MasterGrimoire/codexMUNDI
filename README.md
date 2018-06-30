# Grimoire5e

An ongoing project to keep track of D&amp;D stuff. These files are compatible with the Grimoire 5e iOS app (to be released sometime 2018). While excellent XML files already exist, it was important to keep control of the data format, in order to for Grimoire 5e to maintain an extremely high level of efficiency and presentability.

### Why not XML?
    1. JSON requires less tags than XML – XML items must be wrapped in open and close tags whereas JSON you just name the tag once.
    2. Because parsing JSON objects is faster. Parsing XML software is slow and cumbersome. Many parsing libraries can use large amounts of memory due to the verbosity and cost of parsing large XML files.
    3. JSON data model’s structure matches the data: JSON’s data structure is a map whereas XML is a tree. Although a map (just key/value pairs) can be limiting, that’s what we want, because it is easier to interpret and is predictable.
    4. Same interoperability as XML - no loss there.
    5. JSON is easier to read than XML – Obviously a personal preference.


## Models

These files model the D&D universe by splitting it into eight categories:
    - Items
    - Backgrounds
    - Feats
    - Spells
    - Races
    - Classes
    - Monsters
    - Unearthed Arcana

It is my hope that the community will help to keep these files updated as new content is released.
