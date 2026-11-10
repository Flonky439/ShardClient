# ShardClient

A client-side utility mod for **A Township Tale on Meta Quest**. It runs on your own game,
so it works on community servers that don't have it installed.

Download: **[latest release](https://github.com/Flonky439/ShardClient/releases/latest)**
(`ShardClient.dll`). Already installed? Type `shard update` in the console instead (see
[Updating](#updating)).

---

## What you need

- A Meta Quest with **A Township Tale** installed from the Meta store.
- A **PC** (Windows is easiest; Mac or Linux work with SideQuest) and a **USB cable** that
  carries data. You only need the PC for setup: updates happen in the headset.

## Step 1: Developer mode

Your headset has to allow files and apps from a PC.

1. Sign in at [developers.meta.com](https://developers.meta.com/horizon/) with your Meta
   account and create an organisation (any name). Meta requires this before developer mode
   can be switched on.
2. In the **Meta Horizon** app on your phone: **Menu → Devices →** your headset **→ Headset
   settings → Developer mode → on**.
3. Restart the headset.
4. Plug it into the PC. In the headset, accept **Allow USB debugging** (tick *Always allow
   from this computer*).

## Step 2: SideQuest

Install **SideQuest (Advanced Installer)** from [sidequestvr.com](https://sidequestvr.com/setup-howto).
With the headset plugged in, the dot in its top-left corner turns green. You'll use it to
copy files onto the headset.

## Step 3: LemonLoader (the mod loader)

LemonLoader is MelonLoader for Android/Quest. It modifies your installed copy of the game so
it loads mods. ShardClient is built for **LemonLoader 0.6.5.1**. Get it only from its
official GitHub: **[LemonLoader releases](https://github.com/LemonLoader/MelonLoaderInstaller/releases/latest)**.

> **Patching resets the game's local data on the headset** (its settings and saved login).
> Back up anything you need from `Android/data/com.Alta.ATownshipTale/` first.

**From a Windows PC (recommended):**

1. Download `lemoninstaller-win-x64.zip`, unzip it, and run `MelonLoader.Installer.App.exe`.
2. With the headset plugged in, pick it and press **Use this Device**.
3. Find **A Township Tale** (`com.Alta.ATownshipTale`) in the list and press **Patch**.
   Keep the headset awake until it says **Patched**.

**From the headset (Mac or Linux PC):**

1. Download `com.lavagang.melonloader.installer.apk` and drag it onto SideQuest's
   **Install APK** button (the box-with-arrow icon at the top).
2. In the headset, open **Library → Unknown Sources → MelonLoader Installer** and grant
   the permissions it asks for.
3. Pick **A Township Tale**, press **Patch**, and say **Yes** to uninstall and **Install**
   to reinstall when asked.

**Then, either way:**

- The Quest may warn that the app was modified and offer to restore it. Press **Close** or
  **Open App**, never *Restore*.
- If the Quest library says the game isn't installed, restart the headset.
- The **first launch is slow** (several minutes, sometimes 20+). Let it finish.

## Step 4: Community server mods

Community servers on Quest also need Modding Tavern's Quest mods (for logging in and voice).
ShardClient doesn't include them. Get them from the
[Modding Tavern](https://github.com/ModdingTavern) community and put them in the same
`Mods` folder as ShardClient (Step 5).

## Step 5: ShardClient

1. Download `ShardClient.dll` from the [latest release](https://github.com/Flonky439/ShardClient/releases/latest).
2. In SideQuest, open the file browser (folder icon, *Manage files on the headset*) and go to:

   ```
   Android/data/com.Alta.ATownshipTale/files/MelonLoader/com.Alta.ATownshipTale/Mods/
   ```

3. Drag `ShardClient.dll` into that `Mods` folder.
4. **Fully close** the game and start it. Going to the Quest home screen does *not* close
   it: quit from inside the game, or close it from the Quest's app bar.

## Step 6: First run in the headset

Some features start **off**. You turn things on from the ShardClient console.

1. In a world, raise your wrist to open the quick menu and tap the **ShardClient** bubble.
2. Tap **Console** (it reads SHOWN). A floating panel with a VR keyboard appears.
3. On the console, set the lever to **Run On Client**, type with the VR keyboard and submit.
4. Try `shard help`, then `shard list`.

The bubble's other button, **Dev tools**, switches the console system off and on (it's on to
start; a change needs a full restart).

## Using it

`sc` works as a short form of `shard`.

| Command | What it does |
| --- | --- |
| `shard help` | every command |
| `shard list` | every setting and its value |
| `shard set <Setting> on/off` | turn a feature on or off, e.g. `shard set Telekinesis on` |
| `shard me` | your held item, health and hunger |
| `shard players` | who's on the server, and how far |
| `shard tp <name>` | teleport to a player; searches the map if they're out of range |
| `shard markers` | player markers the map board shows |
| `shard find <name> [metres]` | nearest loaded objects matching a name |
| `shard vault ...` | a personal library of *local copies* of items (`shard vault help`) |
| `shard attach` / `shard detach` | stick a held arrow, knife or spear into what you aim at, or pull it out |
| `shard update` | install the newest version (then restart) |
| `shard locks` | settings the mod's owner has locked (see [Owner locks](#owner-locks)) |

### Features

| Setting | Starts | What it does |
| --- | --- | --- |
| `AirGrab` | on | grip empty air to hang and pull yourself around |
| `UnlockEverything` | on | climbing without the unlock |
| `InfiniteClimbStamina` | on | hand stamina doesn't drain while climbing |
| `ThrowMultiplier` | 3 | how hard letting go of a climb flings you (1 = normal) |
| `BeltGrab` | off, locked | take items from other players' belt and shoulder slots |
| `AnyConnect` | on | any crafting port accepts any part with a port (the server may refuse it) |
| `AutoRevive` | on | when downed, your revive orbs are pulled into your right hand: hold it at your face |
| `Telekinesis` | off | right hand: grip to lock the nearest item along your arm, yank back to pull it in |
| `MineAnything` | off | mine any ore with anything that deals damage |
| `PerfectSwings` | off | every hit counts as a full-strength swing |
| `ForceField` | off | nearby projectiles and creatures pass through you, on your screen only |
| `SnatchFromHands` | off, locked | grab items out of other players' hands |
| `TabletTeleport` | off | a Teleport button on players in the social tablet |

### Owner locks

ShardClient's owner can lock any setting on or off, for everyone or for one player, so
features can be switched off if they cause trouble on servers. A locked setting shows
`(locked)` in `shard list`, and `shard set` won't change it. `shard locks` lists what's
locked for you. `BeltGrab` and `SnatchFromHands` start locked off.

How it works: the mod downloads [`policy.txt`](policy.txt) from this repo when the game
starts and every five minutes after. The file is signed, and the mod refuses one that
isn't signed by the owner. Nothing about you is sent: it's a plain download, and rules
for one player are matched on your headset against your own username.

### What it can't do

The server decides your health, items and stats. ShardClient can't make you invincible or
spawn real items: vault items are local copies only. Some things (like `AnyConnect`) hold on
some servers and only look connected on others; that's the server's choice.

## Updating

In the console: `shard update`. It downloads the newest release from this page into your
Mods folder, checks it against its published checksum, and tells you to restart. `shard
update check` only tells you whether there's a newer version.

## Troubleshooting

- **Crash on the first launch after installing or updating**, usually while joining: start
  the game again.
- **Nothing happens**: make sure the file is in the `Mods` folder above (not
  `/sdcard/MelonLoader/`), and that you fully closed the game.
- **Log**: `Android/data/com.Alta.ATownshipTale/files/MelonLoader/com.Alta.ATownshipTale/MelonLoader/Latest.log`.
  Search it for `ShardClient`.

## Server owners

Running a community server and fighting lag (the forest especially)? **[ShardPerformance](https://github.com/Flonky439/ShardPerformance)** is a separate server-side mod that trims forest and item streaming for areas no player is near. It installs on the server only — players need nothing. (Experimental.)

---

Use at your own risk. ShardClient isn't made by or affiliated with Alta or Modding Tavern.
Copyright © 2026 Flonky439. All rights reserved: you may install and use ShardClient, but not modify
or redistribute it.
