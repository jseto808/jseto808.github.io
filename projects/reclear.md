---
layout: project
type: project
image: img/reclear/reclear-sq.png
title: "Re:CLEAR"
date: 2026-05-08
published: true
labels:
  - Game Development
  - Unity
  - C#
  - 3D
summary: "A tactical FPS situation trainer built in Unity, designed to help players of games like Valorant and CS:GO drill room-clearing scenarios against configurable AI opponents."
---

<div class="text-center p-4">
  <iframe width="720" height="405" src="https://www.youtube.com/embed/Z-xn5f7Wj6o" title="Re:CLEAR Prototype Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen class="mb-3"></iframe>
  <iframe width="720" height="405" src="https://www.youtube.com/embed/3u8eo-_Cgxo" title="Re:CLEAR Final Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Project Summary

Re:CLEAR is a first-person shooter built in Unity, designed as a situation trainer for tactical games like Valorant and CS:GO. The player enters a prototype map populated with armed AI opponents and must clear the room. When the last enemy goes down, a stats screen shows shot accuracy, headshot percentage, deaths taken, and completion time. A built-in reset system lets you retry the exact same scenario instantly without reloading the scene, keeping the focus on drilling the situation repeatedly.

## Gameplay

Each session starts with a configurable number of bots spawned at randomized positions across the map. The player fights through the space using standard FPS controls. Bots patrol, react to sound, seek cover, and retreat when low on health. The player can also plant a bomb to force the bots to respond, adding a defend-the-defuser wrinkle to the encounter. On clearing all enemies, a performance summary appears showing:

- **Shot accuracy**: shots hit / shots fired
- **Headshot accuracy**: critical hits / shots hit
- **Deaths taken**
- **Completion time**

The reset button restores every object in the scene to its original state and repositions the bots without triggering a scene reload, so retry latency is near zero.

## Systems

### Bot AI

Each bot runs a six-state machine: Patrol, Alert, Engage, Retreat, SeekLOS, and Defuse.

During **Patrol**, bots walk between a set of assigned waypoints. When the player makes noise (gunfire, footsteps), the **Sound Alert System** broadcasts the event. Bots within hearing range snap to face the source and transition to **Alert**; bots outside that range are sent to patrol toward it as a secondary response. Once a bot has line of sight to the player for long enough to satisfy a configurable reaction time, it switches to **Engage**.

In **Engage**, bots rotate to track the player, fire in bursts, strafe sideways after each burst, and fall back to the nearest unoccupied cover point between engagements. If health drops below a configurable threshold, the bot transitions to **Retreat**, moving away from the player before seeking cover. If line of sight is lost, the bot enters **SeekLOS** and navigates toward the player's last known position.

### Bomb Mechanic

The player can plant a bomb by holding the designated key near the bomb site. Once planted, the `SoundAlertSystem` notifies all living bots and designates one as the defuser. The designated bot navigates to the bomb and begins defusing; other bots push toward the player to buy time. The defuse includes a checkpoint at the halfway point so the bot does not restart from scratch if its defuse is interrupted.

### Environment Reset

A static `EnvironmentResetter` tracks every `Resettable` component in the scene. On reset, it increments a generation counter that all scene systems subscribe to. Resettables restore position, rotation, health, ragdoll state, and explosive state for every tracked object. The `BotSpawnManager` listens for the generation change and teleports bots back to their assigned spawn points rather than destroying and recreating them, avoiding audio initialization hitches on rapid retry.

### Match Stats

`MatchStats` is a static class that tracks shots fired, shots hit, critical hits, deaths, and session start time. All relevant systems write to it directly. When `SoundAlertSystem` detects that all bots are dead, it calls `MatchStats.RecordSuccess()`, which calculates completion time and triggers the success screen.

## What I Learned

Building Re:CLEAR pushed me to think about AI behavior as a composition of simple, well-separated states rather than a large conditional block. Getting the sound alert propagation right, where nearby bots react directly while farther bots are nudged toward the area, made the bots feel more like a coordinated team rather than independent actors. The environment reset system was an interesting design challenge: storing initial state at startup and diffing against a generation counter turned out to be far more reliable than trying to manage teardown and re-initialization manually. Overall the project reinforced how much game feel comes from the small details, like the burst-strafe rhythm, the retreat threshold, and the near-zero retry delay.
