---
layout: project
type: project
image: img/psycho-puppy/psycho-puppy.png
title: "Psycho Puppy"
date: 2026-02-18
published: true
labels:
  - Game Development
  - Unity
  - C#
  - 3D
summary: "A 3D Unity game where you play as a puppy chasing birds across a platform, gaining speed with every catch until you lose control entirely."
---

<div class="text-center p-4">
  <iframe width="720" height="405" src="https://www.youtube.com/embed/rFvWPyQblz8" title="Psycho Puppy Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Project Summary

Psycho Puppy is a 3D game developed in Unity. You play as a puppy running around a platform, collecting birds to rack up a high score. Each bird you catch permanently increases your speed. Collect too many and you go "psycho," losing directional control and charging forward uncontrollably until you crash into a wall.

## Gameplay

The core loop is built around an escalating speed mechanic. Birds wander the platform and flee when you get close, so catching them requires chasing them down. Every catch boosts your movement speed slightly. As speed climbs, the game becomes harder to control. Once you cross the threshold, the game locks you into a full sprint in whatever direction you are facing. A warning UI and sound effect signal when you have crossed the point of no return. Your run ends when you hit a wall.

## Systems

### Player Movement

The player uses Unity's `CharacterController` with snappy jump physics: a fall multiplier adds extra gravity on the way down, and a low-jump multiplier cuts the arc short when the jump button is released early. Rotation is smoothed using `SmoothDamp` to prevent twitchy turns from analog stick input, with a small deadzone to filter out drift. When speed exceeds the uncontrollable threshold, forward input is forced to 1 and the player can only steer.

### Bird AI

Each bird runs a simple state machine with three behaviors: wander, flee, and recover. Birds hop along the ground at a regular interval, picking a new random direction every few seconds while wandering. When the player enters a set radius, the bird switches to flee mode, hopping faster and running in the opposite direction. Hysteresis prevents the bird from flickering between states by requiring the player to move farther away before fleeing stops.

If a bird ends up elevated above the platform, it enters a recovery mode that steers it back toward the ground. A stuck-detection check runs on a short interval: if the bird has not moved enough between checks, it picks a sidestep direction perpendicular to its target and briefly moves that way before resuming recovery. Birds also chirp on a sound timer and play hop animations.

### Bird Spawner

A spawner drops birds from above the platform on a repeating timer, randomizing spawn position across a large area. A cap limits how many birds can exist at once, so the spawner skips a cycle if the live count is already at the maximum.

### Camera

The follow camera tracks the player with a yaw-based offset so it rotates with the player's horizontal turns while keeping a fixed downward tilt. Position and rotation are both lerped each frame for smooth following without snapping.

## What I Learned

Building Psycho Puppy gave me hands-on experience with Unity's `CharacterController`, physics feel tuning, and practical AI state machines. Implementing the bird flee behavior with hysteresis taught me how a small detail like a wider stop-distance prevents visually noisy state transitions that break immersion. The stuck-recovery sidestep system was the trickiest part to get right, since birds could get wedged at the platform edge and spin in place without it. I also got practice structuring gameplay feedback loops: the speed escalation, warning UI, and audio cue work together to build tension before the loss condition hits.
