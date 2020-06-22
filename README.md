# Wires Idea For Shapezio
By : **TDStuart** <br>
Other Contributers : `none :(` <br> <br>
**Note :** For revisions see bottom of page.

**If you wish to add your own idea (seperate from mine) dm me and ill add it to the github with credit. This will allow your idea to more easily be seen by tobspr**

## General Idea
**Here is the base idea :**

**Goal -** Players build big contraptions to make specific shapes, but building all new processing for each new shape is a pain and takes a bunch of space, so players will often build each processing place they may need (cutters, coloring, combiners, etc.). The problem with this is going in and connecting the right belts to take each shape to the right place then connecting it all back together. This is where wires can come in. Wires allow for players to auto-mate the switching of making different shapes without having to manually connect a bunch of belts together. Wires paired with switches and a display of some kind could allow for major automation in the late game, giving rise to mega factories that can be far more complex but also rewarding and add a shift in dynamic for the late game.
<br><br>
**Things Needed -** Well yes wires but here is what else we need <br>
`Switches` <br>
`Display Output (1 Tile on/off)` <br>
`Micro-Controller (Connect Wires to Buildings)` <br>
`And Gate` <br>
`Or Gate` <br>
`XOR Gate` <br>
`Wire Bundles` <br>
`Latches` <br> <br>

## Wire Bundles
Instead of connecting wires like belts, wires should be in a wire bundle. The wire bundle will then connect and act like a belt. This makes a lot more sense as I suspect a lot of wires will be needed. This also will make the micro-chip idea a lot better. Basically players should be allowed to earn upgrades for how many wires they can have in a wire bundle. Probably allow 2 and make it so players need to upgrade the amount to be able to use the full benefits of the micro-chips and save space. <br><br>

Wires should be labeled inside the bundle (either with numbers or colors).

## Micro Controller
Micro-Controller allows wires to interact with buildings. This allows for checking if a building is clogged, disabling a building, enabling a building, etc. Also specific building based things like reading the amount of shapes stored in a storage.

### Belts
**Inputs :** <br>
`Block Belt` (true / false) <br>
`[Check] Shape on Belt` (needs true) <br>
`[Check] Check Is Blocked` (needs true) <br>
**Outputs :** <br>
`Is Blocked` <br>
`Shape On Belt` (true / false) <br>

### Balancer
**Inputs :** <br>
`Block Balancer [1]` (true / false) <br>
`Block Balancer [2]` (true / false) <br>
`[Check] Is Blocked [1]` (needs true) <br>
`[Check] Is Blocked [2]` (needs true) <br>
`[Check] Shape In Balancer` (needs true) <br>
**Outputs :** <br>
`Is Blocked [1]` (true / false) <br>
`Is Blocked [2]` (true / false) <br>
`Shape In Balancer` (true / false)

### Merger
**Inputs :** <br>
`Block Merger Output` (true / false) <br>
`Block Merger Input` (true / false) <br>
`[Check] Is Output Blocked` (needs true) <br>
`[Check] Is Input Blocked` (needs true) <br>
`[Check] Shape In Merger` (needs true) <br>
**Outputs :** <br>
`Is Output Blocked` (true / false) <br>
`Is Input Blocked` (true / false) <br>
`Shape In Merger` (true / false)

### Tunnel
**Inputs :** <br>
`Block Tunnel` (true / false) <br>
`[Check] Is Blocked` (needs true) <br>
`[Check] Shape In Tunnel` (needs true) <br>
**Outputs :** <br>
`Is Blocked` (true / false) <br>
`Shape In Tunnel` (true / false)

### Extractor
**Inputs :** <br>
`Block Extractor` (true / false) <br>
`[Check] Is Blocked` (needs true) <br>
**Outputs :** <br>
`Is Blocked` (true / false) <br>

### Cutter
**Inputs :** <br>
`Block Cutter` (true / false) <br>
`[Check] Is Blocked [1]` (needs true) <br>
`[Check] Is Blocked [2]` (needs true) <br>
`[Check] Shape In Cutter` (true / false) <br>
**Outputs :** <br>
`Is Blocked [1]` (true / false) <br>
`Is Blocked [2]` (true / false) <br>
`Shape In Cutter` (true / false) <br>

(didn't finish all because I got bored lmao)


## Wires
First off I think having 2 kinds of wires can solve multiple problems, although it makes the programing more complex and can confuse players. <br>

What I mean when I say 2 types of wires are **instant** wires and **tick** wires. Instant wires are only calculated when a user inputted change occurs and is calculated all at one time with no pausing. Tick wires are calculated every tick, can carry pulses, and have more flexibility like being able to do loops and advanced wiring. <br>

So if **tick** is more advanced why not use it all the time? Well it is slow. Unlike in the real world calculations take time and if a wiring makes a loop then it will crash the game. So instead of calculating everything we limit the calculations to be every tick. This will make large wiring slower but will prevent crashes. Since not everything will need loops or more advanced wiring **instant** wiring can prevent the player from experiencing this slowness with most things, as most things won't require **tick** wiring.

### Instant Wiring
Every wire calculation takes place before anything else, all happening the frame the initial update happens. Wire Calculation updates can only be called by the player or by specific things, but in general no loops, no micro-controller output updates, etc. This helps improve performance although an initial lag spike may occur for larger circuits (Maybe introduce a delay to spread the load? although defeats the "instant" wiring name lmao).

**Side Effects :** <br>
Only player initiated wiring calculations. <br>
All wiring calculations completed before calculating something else. <br>
No pulses. <br>
No wire can change itself. <br>
No loops. <br>

### Tick Wiring
Every wire calculation happens a tick after one another. The first calculation happens when it gets called but the next calculation will be pushed off to the next tick (aka next frame).

### Switching Wire Types
Users should just be allowed to click on the wire and change its type!

## Analytics
I think analytics of the wiring performance and operations would be very useful. Not only to keep in check how much game performance is impacted by what kinds of things and try to optimize but also to keep track of everything going on in complex wiring. There can also be settings that delay wiring speed for game performance which would be useful to know if you should use.
