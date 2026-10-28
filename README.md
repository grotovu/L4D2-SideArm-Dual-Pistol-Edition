# [L4D2] SideArm (Dual Pistol Edition)

A modified version of [NoroHime's SideArm plugin](https://forums.alliedmods.net/showthread.php?t=340647) for *Left 4 Dead 2*. 

This plugin allows players carrying a melee weapon or chainsaw to temporarily swap to a sidearm without dropping their melee weapon. This specific build modifies the original behavior to grant **Dual Pistols (Akimbo)** instead of a single pistol.

---

## 🌟 What This Plugin Does

In vanilla *Left 4 Dead 2*, picking up a melee weapon replaces your secondary slot completely, leaving you without any ranged option if you get boomer-biled, need to shoot distant targets, or want to pick off smokers from afar.

With this plugin:
* Pressing your configured key (default: **Zoom / Middle Mouse Click**) temporarily stashes your melee weapon or chainsaw and gives you a sidearm.
* Pressing the key again, switching weapons, or changing maps safely returns your stored melee weapon or chainsaw with all clip and fuel ammo preserved.
* **Dual Pistol Modification:** When swapping to your sidearm, you are equipped with **Dual Pistols (30 rounds)** rather than the single default P220 / Glock.

---

## 🔧 Changes in This Build

* **Dual Pistols by Default:** Modified the weapon pemberian routine so that swapping to a sidearm automatically gives a secondary pistol to activate dual-wielding.
* **State Preservation:** Retains clip capacity, extra ammo, and chainsaw fuel across stashes and swaps.

---

## 📦 Installation

1. Compile `l4d_sidearm.sp` into `l4d_sidearm.smx` using SourceMod 1.11+.
2. Place `l4d_sidearm.smx` into your server's `left4dead2/addons/sourcemod/plugins/` directory.
3. *(Optional)* Place `l4d_sidearm.phrases.txt` into `left4dead2/addons/sourcemod/translations/` for on-screen notification hints.

> **Note on Weapon Drop Plugins:**  
> If your server uses a weapon drop plugin, standard versions may conflict when dropping stashed weapons. Use [HarryPotter's l4d_drop (v1.10+)](https://github.com/fbef0102/L4D1_2-Plugins/tree/master/l4d_drop) to prevent issues.

---

## ⚙️ Configuration (CVars)

The config file will automatically be created at `left4dead2/cfg/sourcemod/l4d_sidearm.cfg`:

| CVar | Default | Description |
| :--- | :---: | :--- |
| `sidearm_announce` | `"2"` | Notification type when sidearm is ready: `0` = Off, `1` = Center Text, `2` = Chat, `4` = Hint Box *(add numbers together for combinations)*. |
| `sidearm_key` | `"524288"` | Key bitflag to trigger swap. Default `524288` corresponds to `IN_ZOOM` (middle click). |
| `sidearm_holdtime` | `"0.0"` | Time in seconds to hold the button to swap sidearms. Set to `0.0` for instant tap mode. |

### Key Bitflag Reference
If you want to rebind `sidearm_key`:
* `IN_ZOOM` (Zoom / Middle Click): `524288`
* `IN_USE` (E / Use Key): `32`
* `IN_RELOAD` (R / Reload Key): `8192`
* `IN_SPEED` (Shift / Walk): `131072`

---

## 💡 Optional: Removing the "Item Pickup" HUD Pop-up

### The Side Effect
Because this fork gives a second pistol to enable akimbo dual-wielding, the game engine considers each toggle as picking up a new item. This triggers the floating pistol pickup icon on your HUD every time you switch.

### The Fix (`HudLayout.res`)
You can completely hide the floating pickup notification by setting `CItemPickupPanel` off-screen.

If you already use a custom HUD or a **Crosshair Support Base** addon from the Steam Workshop, extract its `scripts/HudLayout.res` (or `Resource/HudLayout.res`) and apply the following:

#### 1. Disable the Pickup Panel
Locate or add `CItemPickupPanel` and set its position off-screen:
```res
	CItemPickupPanel
	{
		"fieldName"		"CItemPickupPanel"
		"xpos"			"10000"
		"ypos"			"10000"
		"wide"			"f0"
		"tall"			"f0"
		"visible"		"0"
		"enabled"		"0"
		"PaintBackgroundType"	"0"
		"usetitlesafe"		"0"
	}
```
---

## 📜 Credits & Acknowledgments
* **[NoroHime](https://forums.alliedmods.net/showthread.php?t=340647)** - Original author of the `[L4D2] SideArm` SourceMod plugin.
* **little_froy** - Origin of the stashed sidearm concept.
