# Grimoire 5e JSON Data File Repository

This is an ongoing project to keep track of D&amp;D files. These files have been designed to be compatible with the 'Grimoire 5e' iOS app (release date sometime in Q3 2018 as I'm told by the developer).

It is my hope that the community will help to keep these files updated as new content is released - as well as to fix typos or other mistakes. Gooooo collaboration!


## How to use these files in your app

Make sure that you are on the 'master' branch. Look for the green button that says 'Clone or download'. Download the files to your computer, or save them to your icloud drive. From there, import them into the Grimoire app.

These files contain all of the content from the following:
  - Player's Handbook
  - Dungeon Master's Guide
  - Monster Manual
  - Volo's Guide to Monsters
  - Xanathar's Guide to Everything
  - Sword Coast Adventurer's Guide
  - Mordenkainen's Tome of Foes

It also contains all the monsters, items, and character options from the published adventures, as well as the Elemental Evil Player's Companion.


## How to Contribute

If you are not familiar with the git workflow, I suggest you do some reading up on it. It seems daunting, but it's really quite easy once you get the hang of it. Once you are ready to make some contributions or changes, fork the repo, make your changes in your own repo and then click "New Pull Request". Make sure that 

Afterwards, pull the repo. Please make sure to create your own branch with a descriptive name, in the fork. Branch names should have the following format:

    category/feature_name

    example if adding one item:
    items/vorpal_sword

    example if adding several spells:
    spells/adding_three_spells

    example if making a prearranged large feature
    monsters/mordenkainens_tome_of_foes_part2

Ensure that your commits are clear and concise, and would easily finish the following sentence: "This commit will..."

    example commit:
    "Fix a typo in Aid spell"
    or
    "Add three monsters from Mordenkainen's Tome of Foes"

Note: when adding objects to a file, it is preferred that they are added at the end of the file. It is good practice to keep a limit on changes. Unwieldy, large PR's must be discussed beforehand; generally, however, they will be rejected. Adding five objects to a file is considered acceptable; more is considered unwieldy. If comments are made to your PR, please address them in a timely fashion. After a PR has been approved, it will be merged in by a moderator and that branch will be deleted. As such, make sure to not have anything else that you need there.

**Review turnaround times:** I will strive to get to all reviews within a week of them being posted. Most of the time it will be sooner. After a week, you may ping me to ask to for a review if there's been no activity.


## Why JSON and not XML?

It seems that the overall preference of the users that have made these types of files available to the D&D community has been to use XML files. The developer of Grimoire 5e seems to have taken a different approach and decided to use JSON files for the following reasons:

  1. JSON requires less tags than XML – XML items must be wrapped in open and close tags whereas JSON you just name the tag once.
  2. Parsing JSON objects is faster. Parsing XML is slow and cumbersome. Many parsing libraries can use large amounts of memory due to the verbosity and cost of parsing large XML files.
  3. JSON data model’s structure matches the data: JSON’s data structure is a map whereas XML is a tree. Although a map (just key/value pairs) can be limiting, that’s what we want, because it is easier to interpret and is predictable.
  4. Same interoperability as XML - no loss there.
  5. JSON is easier for humans to read than XML – Obviously a personal preference, but very important for seeing exactly what you're dealing with.


## Organization & File Structure

These files model the D&D universe by splitting it into eight categories:
  - Items
  - Backgrounds
  - Feats
  - Spells
  - Races
  - Classes
  - Monsters
  - Unearthed Arcana

Because of the plethora of sorting functions to view items/monsters/etc. in the app makes finding anything quite easy, it was decided that, rather than maintaining several different file sets for different addons (Modern items, or PHB compendiumn, Volo's compendium, etc), it would be more efficient to maintain a file for each category. Certainly, this means you have to import each file separately. While this may seem cumbersome, it is much less cumbersome than attempting to maintain a JSON file of a nearly a million lines. Finally, it is of no importance that objects within the JSON blobs be in any particular order - alphabetical or whatever. However, when adding objects to a file, it is preferred that they are added at the end of the file helping to establish a chronology of items added.

Why is Unearthed Arcana separate? Not everyone wants that content. The idea is to have official content easily accessible with Unearthed Arcana, or your own homebrew files loaded on top.

Generally, the JSON files will have the following structure, with the exception of Unearthed Arcana. Any new objects that are added, must be added in the respective files, within the respective brackets. For example, the CodexITEMS.json file will look like this:

    {
        "item": [
            {
                YOUR OBJECT HERE
            }
        ]
    }

Unearthed Arcana will contain all the categories together. The template that I've been given by the developer which contains the Deault SRD Open Gaming Content is arranged in this fashion - which explains why the other files have a seemingly unnecessary top level json blob.

    {
        "item": [
        ],
        "monster": [
        ],
        "spell": [
        ]
        etc...
    }


## Model structure

In this section, I will outline the expected JSON tags for each category - these are based on a default template I've received from beta testing the Grimoire's import file option. Failing to adhere to these tags and structure will cause your PR to be rejected.

### codexSPELLS.json

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | ---------
name | String | "Magic Missile" | Y |
srdContent | Boolean | false | Y | If this item is part of SRD content, this should be true. Otherwise, false.
module | String | "core" | Y | Options:<br>  - core<br>  - modern<br>  - renaissance<br>  - futuristic<br>  - wuxia-chinese<br>  - wuxia-japanese<br>  - unearthedArcana
level | Integer | 0 | Y | Spell levels - 0 being cantrips
school | String | "A" | Y | Options:<br>  - A (Abjuration)<br>  - C (Conjuration)<br>  - D (Divination)<br>  - EN (Enchantment)<br>  - EV (Evocation)<br>  - I (Illusion)<br>  - N (Necromancy)<br>  - T (Transmutation)
ritual | Boolean | true | Y |
time | String | "1 action" | Y |
range | String | "30 feet" | Y |
components | String | "V, M (a tiny strip of cloth)" | Y |
duration | String | "8 hours" | Y |
classes | String | "Rogue (Arcane Trickster), Cleric, Paladin" | Y | Classes should include a base class ("Rogue") and, if applicable, an extension class in parantheses. Classes should be separated by a comma and a space
text | String Array | ["Example one", "Example two"] | Y | Description of the spell
source | String | "Player's Handbook p. 123" | N | It is preferred to have this included, for ease of location of item in source material.


### codexITEMS.json

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | ---------
name | String | "Sling Bullets" | Y |
srdContent | Boolean | false | Y | If this item is part of SRD content, this should be true. Otherwise, false.
module | String | "core" | Y | Options:<br>  - core<br>  - modern<br>  - renaissance<br>  - futuristic<br>  - wuxia-chinese<br>  - wuxia-japanese<br>  - unearthedArcana
type | String | "HA" | Y | Options:<br>  - A (Ammunition)<br>  - HA (Heavy Armor)<br>  - R (Ranged)<br>  - $ (Currency)<br>  - LA<br>  - MA (Medium Armor)<br>  - G (Gear)<br>  - W (Wondrous)<br>  - M (Melee)<br>  - ST (Staff)  - RD (Rod)<br>  - S (Shield)<br>  - SC (Scroll)<br>  - WD (Wand)<br>  - RG (Ring)<br>  - P (Potion)
magic | Boolean | true | N | Wether the item in question is a magical item or not. If tag is not present, item is assumed to be non-magical
rarity | String | "uncommon" | N | Rarity and/or attunment requirements
weight | Double | 0.25 | N | Item weight, in lbs. Can be an integer (ie. 4 is fine. 4.0 is not needed)
text | String Array | ["Hot to touch", "Super sharp"] | Y |
source | String | "Player's Handbook p. 123" | N | It is preferred to have this included, for ease of location of item in source material.
ac | Integer | 9001 | N | Indicates if item provides an Armor Class rating while being worn
strength | Integer | 2 | N | Indicates if item has a strength requirement to being worn
stealth | Boolean | true | N | Set to 'true' if item provides a STEALTH DISADVANTAGE. If this is not present, it is assumed it is false
dmg1 | String | 1d5 | N | On weapon items, indicates the primary damage the weapon does
dmg2 | String | 1d8 | N | On weapon items, indicates the secondary damage the weapon does
dmgType | String | "P" | N | On weapon items, indicates the type of damage that weapon does
property | String | "M, T, V" | N | On weapon items, indicates the weapon properties. Options:<br>  - P (Piercing)<br>  - F (Finesse)<br>  - H (Heavy)<br>  - 2H (Two Handed)<br>  - V (Versatile)<br>  - T (Thrown)
range | String | "20/60" | N | On throwable items, indicates range that it can be thrown, in feet
modifier | MODIFIER<br>or<br> MODIFIER Array | See **Custom JSON Objects** below for details | N | Includes modifier details about the item


### codexBACKGROUNDS.json

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | ---------
name | String | "Acolyte" | Y |
srdContent | Boolean | false | Y | If this item is part of SRD content, this should be true. Otherwise, false.
module | String | "core" | Y | Options:<br>  - core<br>  - modern<br>  - renaissance<br>  - futuristic<br>  - wuxia-chinese<br>  - wuxia-japanese<br>  - unearthedArcana
proficiency | String | "Insight, Religion" | Y | Comma separated list of proficiencies
trait | TRAIT Array | See **Custom JSON Objects** below for details | Y |



### codexRACES.json

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | ---------
name | String | "Aarakocra" | Y |
srdContent | Boolean | false | Y | If this item is part of SRD content, this should be true. Otherwise, false.
module | String | "core" | Y | Options:<br>  - core<br>  - modern<br>  - renaissance<br>  - futuristic<br>  - wuxia-chinese<br>  - wuxia-japanese<br>  - unearthedArcana
size | String | "M" | Y | Options:<br>  - T (Tiny)<br>  - S (Small)<br>  - M (Medium)<br>  - L (Large)<br>  - H (Huge)<br>  - G (Gargantuan)
speed | Integer | 25 | Y | Assumed to be in feet
ability | String | "Cha 2, Wis 1" | Y | Any ability bonuses that a race has
proficiency | String | "Stealth" | N | If a race has any natural proficiency for an ability
spellAbility | String | "Constitution" | N | If a race has a natural spell spell affinity, it is noted here
trait | TRAIT<br>or<br>TRAIT Array | See **Custom JSON Objects** below for details | N | Details on the race, each attributed to a specific source


### codexFEATS.json

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | ---------
name | String | "Acrobat" | Y |
text | String Array | ["String 1", "String 2"] | Y |
module | String | "core" | Y | Options:<br>  - core<br>  - unearthedArcana
prerequisite | String | "Gnome (Rock)" | N |
srdContent | Boolean | false | Y | If this item is part of SRD content, this should be true. Otherwise, false.
source | String | "Player's Handbook p. 1" | N | It is preferred to have this included, for ease of location of item in source material.
modifier | MODIFIER<br>or<br> MODIFIER Array | See **Custom JSON Objects** below for details | N |


### codexCLASSES.json

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | -----------
name | String | "Cleric" | Y |
srdContent | Boolean | false | Y | If this item is part of SRD content, this should be true. Otherwise, false.
module | String | "core" | Y | Options:<br>  - core<br>  - modern<br>  - renaissance<br>  - futuristic<br>  - wuxia-chinese<br>  - wuxia-japanese<br>  - unearthedArcana
hd | Integer | 5 | Y | Hit dice
proficiency | String Array | ["Constitution", "Intelligence"] | Y | Class proficiencies for abilities and skills
spellAbility | String | "Intelligence" | Y | Classes spell-casting attribute
numSkills | Integer | 5 | Y | The number of skills the class affords
autolevel | LEVEL Array | See **Custom JSON Objects** below for details | Y | Contains level features of the class
armor | String | "light armor" | Y | The type of armor this class wears
weapons | String | "simple weapons, hand crossbows" | Y | Weapons that the class is proficient with
tools | String | "three musical instruments" | Y | Tools that the class is proficient with
wealth | String | "5d4x10" | Y | The amount of money the class starts with


### codexMONSTERS.json

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | -----------
name | String | "Aarakocra" | Y |
srdContent | Boolean | false | Y | If this item is part of SRD content, this should be true. Otherwise, false.
module | String | "core" | Y | Options:<br>  - core<br>  - modern<br>  - renaissance<br>  - futuristic<br>  - wuxia-chinese<br>  - wuxia-japanese<br>  - unearthedArcana
size | String | "M" | Y | Options:<br>  - T (Tiny)<br>  - S (Small)<br>  - M (Medium)<br>  - L (Large)<br>  - H (Huge)<br>  - G (Gargantuan)
type | String | "fiend (demon)" | Y |
alignment | String | "chaotic evil" | Y |
ac | String | "15 (natural armor)" | Y |
hp | String | "137 (11d12+66)" | Y |
speed | String | "30 ft., climb 40 ft." | Y |
str | Integer | 1 | Y |
dex | Integer | 1 | Y |
con | Integer | 1 | Y |
int | Integer | 1 | Y |
wis | Integer | 1 | Y |
cha | Integer | 1 | Y |
skill | String | "Perception +5, Stealth +3" | Y |
immune | String | "cold" | Y | Damage that the creature is immune to
vulnerable | String | "cold" | Y | Damage that the creature is vulnerable to
resist | String | "cold" | Y | Damage that the creature is resistant to
conditionImmune | String | "cold" | Y | Conditions that the creature is immune to
senses | String | "darkvision 60 ft." | Y |
passive | Integer | 15 | Y | Passive perception
languages | String | "Common" | Y |
cr | String | "1/4" | Y | Challange rating is as a string due to 1/2, 1/4, etc. ratings
trait | TRAIT Array | See **Custom JSON Objects** below for details | N | Details on the creature
reaction | TRAIT object | See **Custom JSON Objects** below for details | N | Details on a specific reaction a creature might have
action | ACTION Array | See **Custom JSON Objects** below for details | N | Actions that creatures can take
legendary | ACTION Array | See **Custom JSON Objects** below for details | N | Legendary actions that a legendary creature can take
extraDetails | String Array | ["String one", "String two"]| N | Extra details on the creature
spells | String | "command, comprehend languages, aid" | N | List of spells available to creature, seperated by a comma and a space
slots | Integer Array | [3, 2, 2, 1] | N | A list of the number of spell slots
source | String | "Player's Handbook p. 123" | N | It is preferred to have this included, for ease of location of item in source material.


### Custom JSON Objects

MODIFIER JSON OBJECT

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | -----------
category | String | "bonus" | Y | Category options are:<br>  -ability score<br>  -bonus<br>  -skills
text | String | "dexterity +1" | Y |


TRAIT JSON OBJECT

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | -----------
name | String | "Language" | Y |
text | String or String Array| "Example text"<br>or<br>[{"Example text", "Example text two"}] | Y |


ACTION JSON OBJECT

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | -----------
name | String | "Paralyzing Touch" | Y |
text | String or String Array| "Example text"<br>or<br>[{"Example text", "Example text two"}] | Y |


LEVEL JSON OBJECT

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | -----------
level | Integer | 1 | Y | The level at which the feature is available
feature | FEATURE | See FEATURE JSON OBJECT | N |
slots | Integer Array | [4, 2, 5] | N | What slots are available at this level
scoreImprovement | Boolean | true | N | If a score improvement is available at this level, this sholud be set to true


FEATURE JSON OBJECT

Tag | Content Type | Example | Required | Notes
----------- | -----------| ----------- | ----------- | -----------
optional | true | 1 | N | The level at which the feature is available
name | String | "Arcane Tradition: School of Abjuration" | Y |
text | String Array | ["Example one", "Example two"] | Y |
source | String | "Player's Handbook p. 123" | N | It is preferred to have this included, for ease of location of item in source material.
proficiency | String | "Arcana" | N | Proficiency given by the feature
