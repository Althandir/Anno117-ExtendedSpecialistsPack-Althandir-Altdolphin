# General Findings:

# Good to know:
- Combining AreaBuff and BuildingBuff is not possible
- Item sets EffectScope

# Only Legendary Items support ItemWithBoost UI! 
- BoostHint visibility via Research does NOT Work on Items with Non-Legendary-Rarity
- When Condition is fullfilled BoostHint on Non-legendary-Items is visible

# Other Findings:
- AssetPool All Wonder Forums (81273) contains Roman Forum AND Celtic Roman Temple? But Localization only names "Forums"

# AreaBuff
- Effect Range is defined in Area Buff
- AreaBuff seems to ignore <IsStackable> and can always stack
- Effect Range: Try using % Based Upgrade. Fixed Number Upgrade seems to have a performance Impact?

# AreaEffects
- Chained AreaEffects are possible
- e.g. Armory -> affects Custodes 
- But UI can't really showcase them
- current Workaround is to let Player know via Description

# Officium Item to increase Slots
- Initially the plan was to add an Item into the Gov Villa to increase the SocketSlotAmount as non-stackable-buff
- But there is an Issue: The Buff gets applied twice when the effect target is equals the source building 
Radius does not work on Guesthouses as they are untargetable via Radius?
Tested: "Local" and "ObjectsInArea" are working
First Buff: as a removable buff granting the effect
Second Buff: same Buff but UNREMOVABLE

This causes the officium always to have increased slots. 
This issue persists even when using other combination of buffs. 
The second "SocketAmoutUpgrade" is applied on the building by itself it breaks the buffs.

E.g. Specialist -> Targets Guesthouses via "ObjectsInArea" with SocketUpgrade +1
- Slotted into Gov = Works as expected - Guesthouses get +1 Slot and -1 Slot when removed
- Slotted into Guesthouse = Bugged - Buff is applied twice and increases permanently SlotAmount

## WORKAROUND: Via 3rd Building and AreaEffect
Item applies BuildingBuff with only AdditionalFunctionalEffect - new Effect targets Guesthouses and Villa - Item behaves as expected when adding and removing.
See: AdditionalSpecialistsGuesthouses-L.xml

# Double <AdditionalFunctionalEffects> are not working as of now. Each Buff can only have one AdditionalFunctionalEffect
# Multiple Buffs per Items are possible
- I would recommend against it as this will cause the Item appearing twice in the Building Overview with only the Effects from the first Buff. Thats very difficult to ecplain to the Player.