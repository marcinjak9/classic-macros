# Redcomrade Fury Warrior macros

## Summary
Last night i passed few hours to study the macro machanics in Classic Wow.
I creted few macros to clean my action bars and keybind most of the functionalities

The main focus was to use key modifiers for spells so one button can act as 2 or 3 spells using CTRL, ALT and SHIFT modifier.
Another focus was about the battle dancing, so the Abilities uses required stance, just to not worry up about switching stance manually.


## Rules
* Damage dealing abilities switches from Battle Stance to Berserker Stance almost every time
* In Defensive Stance only the required abilities switches to other stances (ex Whirlwind)
* The abilities are grouped per type or per similarity, i tried to use modifiers to use same type of ability (ex ALT modifier is mainly for Berserker abilities and aoe, CTRL for Defence)

## Index
  * [Basic Abilities / Queued](#basic-qbilities-or-queued)
  * [Charge Intercept](#charge-intercept)
  * [Proc Macro](#proc-macro)
  * [Panic](#panic)
  * [Tank is Dead](#panic)
  * [Cooldowns](#Cooldowns)
  * [Interrupt](#interrupt)
  * [Taunts](#taunts)
  * [Rage AP](#rage-ap)
  * [Tanky stuff](#tanky-stuff)
  * [PVP God](#pvp-god)
  * [Weapon Swap](#weapon-swap)

# Macros

## Basic Abilities or Queued
### Description:
This macro is a basic macro for main warrior abilities

### Skills: 
  * Heroic Strike
  * Cleave
  * Sunder Armor

### Rules:
  * Targets near enemy and starts attack
  * **shift:** Berserker Stance -> Used ability
  * **alt:** Cleave
  * **ctrl:** Sunder Armor
```
  #showtooltip [mod:alt]Cleave;[mod:ctrl] Sunder Armor; Heroic Strike
  /targetenemy [dead][noharm]
  /startattack
  /cast [form:1,mod:ctrl]Defensive Stance; [mod:shift] Berserker Stance
  /cast [mod:alt]Cleave;[mod:ctrl]Sunder Armor; Heroic Strike
```
### Notes:
  * If in Defensive stance the main ability should be Sunder Armor


## Charge Intercept
### Description: 
Macro that detects if you are in combat or not to Charge or Intercept the target (with Hamstring if needed)
Abilities: 
  * Charge
  * Intercept

### Rules:
  * **nocombat:** Battle Stance -> Charge
  * **combat:** Berserker Stance -> Intercept
  * **alt:** Forces Intercept
  * **shift:** Charge/Intercept -> Hamstring

```
#showtooltip [nocombat]Charge;Intercept
/dismount
/cast [mod:alt]Berserker Stance;[nocombat]Battle Stance
/cast [mod:alt]Intercept;[nocombat]Charge;
/cast [combat]Berserker Stance
/cast  Intercept
/cast [mod:shift] Hamstring
```

### Notes:
  * Maybe alt modifier should just cast the Charge of your current Stance, need testing

## Proc Macro
### Description:
This macro is useful to cast dodge/parry proc abilities in correct stance, and fallbacking to Execute (temporary)

### Abilities:
  * Overpower
  * Revenge
  * Execute

## Rules:
  * **ctrl:** Defensive Stance -> Revenge
  * **alt:** Battle Stance -> Overpower
  * **base:** Execute

```
#showtooltip [mod:ctrl]Revenge;[mod:alt]Overpower;Execute
/cast [mod:ctrl] Defensive Stance; [mod:alt]Battle Stance; Berserker Stance
/cast [mod:ctrl]Revenge;[mod:alt]Overpower;Execute
```

## Panic
### Description:
A simple panic macro, equips the shield and casts Shield wall
### Abilities:
  * Shield Wall

### Rules:
equip shield -> Defensive Stance -> Shield wall -> Scream something

```
#showtooltip Shield Wall
/eq Frostbite
/eq Intricately Runed Shield
/cast Defensive Stance
/cast Shield Wall
/y PANIC MODE!!! SHIELD WALL ON!
```
### Notes: 
Needs double tap in combat (changin weapons in comabt triggers GCD)

### Tank is Dead
### Description:
Just as panic macro but uses AOE Taunt
### Abilities:
  * Shield Wall
  * Challenging Shout

### Rules:
equip shield -> Defensive Stance -> Shield wall -> Challenging Shout -> Scream something -> Die

```
/eq Frostbite
/eq Intricately Runed Shield
/cast Defensive Stance
/cast Shield Wall
/cast Challenging Shout
/y SHIELD WALL AND CHALLENGING SHOUT ON, GL!
```

### Notes: Needs double tap, or even triple (needs to check)

### Cooldowns
### Description:
All cooldowns in one, using the correct stance to cast, fallbacking to Death Wish
### Abilities:
  * Retaliation
  * Recklessness
  * Death Wish

### Rules:
shift: Battle stance -> Retaliation
ctrl: Berserker Stance -> Retaliation
alt: Berserker Stance -> Death Wish -> Retaliation (maybe need double tap)
base: Death Wish

```
#showtooltip [mod:shift]Retaliation;[mod:alt][mod:ctrl]Recklessness;Death With
/cast [mod:shift] Battle Stance;Berserker Stance
/cast [mod:alt][nomod] Death Wish
/cast [mod:shift] Retaliation; [mod:alt][mod:ctrl] Recklessness;
```

### Interrupt
### Description:
Use both interrupts with one macro

### Abilities:
  * Pummel
  * Shield Bash

### Rules:
ctrl: Defensive Stance -> Equip Shield -> Shield Bash (needs double tap in combat)
base: Berserker Stance -> Pummel

```lua
#showtooltip [mod:ctrl][form:2]Shield Bash;[mod:alt][] Pummel
/cast [mod:ctrl][form:2]Defensive Stance;[mod:alt][] Berserker Stance
/cast [noform:2]Pummel
/equipslot 17[form:2] Intricately Runed Shield
/cast[form:2]Pummel;Shield Bash
```

### Taunts
### Description:
Simple macro to taunt with both Taunt and Mocking Blow, can be used on mouseover

### Abilities:
  * Taunt
  * Mocking Blow

### Rules:
if in Battle Stance use Mocking blow
if is Defensive Stance use Taunt
alt: Force Defensive stance and Taunt
base: Defensive Stance and Taunt

```
#showtooltip [mod:shift][form:1,nomod]Mocking Blow;[mod:alt][form:2]Taunt;[form:3]Taunt;
/use [mod:shift]Battle Stance;[nomod]Defensive Stance
/use [@mouseover,harm,form:1][form:1]Mocking Blow;[@mouseover,harm][]Taunt
```

### Rage AP
### Description:
Just Bloodrage, Berserker rage and Battle Shout

### Abilities:
  * Bloodrage
  * Berserker Rage
  * Battle Shout

### Rules:
  * **alt:** Berserker Stance -> Berserker Rage
  * **shift:** Battle Shout
  * **base:** Bloodrage

```
#showtooltip [mod:alt] Berserker Rage;[mod:shift] Battle Shout; Bloodrage
/cast [mod:alt] Berserker Stance
/cast [mod:shift] Battle Shout
/cast [mod:alt] Berserker Rage;[nomod] Bloodrage
```

### notes:
Do both modifier (Bloodrage, Berserker Rage)


## Tanky stuff
### Description: 
Aoe Tanking abilities and debuffs

### Abilities:
  * Sunder Armor (duplicate maybe be removed)
  * Thunder Clap
  * Demoralizing Shout

### Rules:
  * **alt:** Defensive Stance -> Sunder Armor
  * **shift:** Battle Stance -> Thunder CLap
  * **base:** Demoralizing Shout

```
#showtooltip [mod:alt]Sunder Armor;[mod:shift]Thunder Clap; Demoralizing Shout
/cast [mod:alt] Defensive Stance;[mod:shift] Battle Stance 
/cast [mod:alt] Sunder Armor;[mod:shift] Thunder Clap; Demoralizing Shout
```

## PVP God
### Descrption:
Some utilites for pvp and not

### Abilities:
  * Hamstring
  * Intimidating Shout
  * Disarm

### Rules:
  * **alt:** Intimidating Shout
  * **shift:** Defensive stance -> Disarm
  * **base:** Hamstring

```
#showtooltip [mod:alt]Intimidating Shout;[mod:shift]Disarm;Hamstring
/cast [mod:shift] Defensive Stance; [nomod:shift,form:2] Berserker Stance
/cast [mod:shift] Disarm; [mod:alt] Intimidating Shout; Hamstring
```

## Weapon swap
### Descrption:
Collection of used weapons for fast Swap

### Weapons:
  * Main Hand (MH)
  * Off Hand (OH)
  * 2h (2H)
  * 2h PVP (2HPVP)
  * MH and shield (MHSHIELD)

### Rules:
  * **alt:** 2h
  * **shift:** 2h PVP
  * **ctrl:** MH + Shield
  * **base:** DW (mh + of)

```
#showtooltip [mod:alt]"2H";[mod:shift]2HPVP;[mod:ctrl]MHSHIELD;MH
/equpitem 16 [mod:alt]"2H"; [mod:shift]"2HPVP"; MH
/equpitem 17 [mod:ctrl]"SHIELD"; OH
```


