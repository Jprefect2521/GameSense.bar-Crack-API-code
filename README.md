---
description: cip
---

# Common issues/problems

## Anti Virus

Some antivirus vendors perform very intensive real-time monitoring/sandboxing that can interfere with the client. You don't need to disable Windows Defender. Whitelisting may not work. Make sure the antivirus is closed and its drivers are unloaded. You can re-open them after loading the cheat.

## Unsopported Windows version



Windows 10 or newer is required. Some older versions of Windows 10 may not work. Update to the latest version of Windows 10. If you are on Windows 10 or newer and you receive this error, restart your computer and try again.

### Anti-cheat

Some anti-cheat drivers (particularly BattlEye) protect game/Steam processes which can lead to problems.

### "Virtual machine not supported"

Some anti-virus vendors run programs in a virtual machine. If you aren't using an anti-virus, then make sure Hyper-V is disabled.

**Known incompatible vendors:** HitmanPro.Alert

### Client not opening?

If nothing happens when you open the client, then try enabling UAC and restarting Steam. Set it to its default setting, which is one notch from the top.

### Menu shows as a solid black rectangle

Go to CS:GO settings and enable "multi core rendering".

### Menu not displaying or flickering

Remove 'nod3d9ex' from your launch options.

Make sure the Steam overlay is enabled. Check it is enabled in both of these places: - Steam > Settings/Preferences > In-game tab. Check the box next to Enable the Steam Overlay while in-game. - Right-click CS:GO in your Library > Select Properties > Under the General tab, check the box next to Enable the Steam Overlay while in-game.

### Initialization Failed

Can happen if you played a Battleye or EAC protected game, Restart PC or disable the BE/EAC service.

### Client closing right after you open it

Install the game that your subscription is for. Make sure invites understand that Windows 10 or newer is required.

## No game found (previously "Game not found")

Happens if the loader is unable to locate game path your subscription is for. This is something we are going to improve significantly soon. As of now, the easiest way to fix this is installing the game on same disk as your [Steam](https://store.steampowered.com) client lies under.

## Common error codes

| Codes     | Description                                                                                              |
| --------- | -------------------------------------------------------------------------------------------------------- |
| D0015703  | [Out of memory](./#out-of-memory)                                                                        |
| D0001140  | [Antivirus](./#antivirus)                                                                                |
| C0005422  | [Unsupported version of Windows](./#unsupported-version-of-windows)                                      |
| D0001923  | [Anti-cheat](./#anti-cheat)                                                                              |
| D0002000  | Connection problem                                                                                       |
| D0001629  | Game is taking too long to load, use -novid or wait until the main menu to inject                        |
| D000C471  | Game crashed while loading                                                                               |
| D000VM51  | ["Virtual machine not supported"](./#virtual-machine-not-supported)                                      |
| D000D6190 | Incompatible vendor. Fix: Completely uninstall Malwarebytes and restart your computer.                   |
| C000P1506 | Unable to locate system path.                                                                            |
| C00059275 | Process integrity check failed. In this case, contact an administrator.                                  |
| C0000001  | No game found. [No game found (previously "Game not found")](./#no-game-found-previously-game-not-found) |
| D0000641  | Contact an administrator.                                                                                |
