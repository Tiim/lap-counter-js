# Use Case: Count Laps

## Overview

**Use Case ID:** UC-003  
**Use Case Name:** Count Laps  
**Primary Actor:** Timekeeper  
**Goal:** Keep an accurate lap count for each participant during the session and see each participant's distance and pace.  
**Trigger:** Timekeeper taps a participant's tile when the participant completes a lap.  
**Status:** Draft  

## Preconditions

- At least one participant is on the participant list.

## Main Success Scenario

1. Timekeeper briefly taps the tile of the participant who completed a lap.
2. System adds one lap to the participant's count and records the current elapsed session time as the time of the last change.
3. System briefly animates the tile to confirm the tap.
4. System shows the participant's updated lap count, distance and pace per 100 m.
5. System colours the tile from green towards red as the time since the participant's last change grows.

## Alternative Flows

### A1: Correct a Miscounted Lap

**Trigger:** Timekeeper presses and holds the tile instead of tapping it (step 1)  
**Flow:**

1. System subtracts one lap from the participant's count and records the current elapsed session time.
2. Use case continues at step 3.

### A2: Press Cancelled

**Trigger:** The pointer moves or the touch is cancelled before the press ends (step 1)  
**Flow:**

1. System leaves the lap count unchanged.
2. Use case ends.

### A3: No Distance Yet

**Trigger:** The participant's distance is zero (step 4)  
**Flow:**

1. System shows the distance as 0 m and leaves the pace blank.
2. Use case continues at step 5.

## Postconditions

### Success Postconditions

- The participant's lap count and time of last change are stored in the browser and survive a page reload.
- Every other open Lap Counter tab in the same browser shows the updated count.

### Failure Postconditions

- The participant's lap count is unchanged.

## Business Rules

### BR-001: Tap and Hold

A short press adds one lap; a press held for 500 ms or longer removes one lap.

### BR-002: Distance

Distance equals the lap count times the lap length (UC-001 BR-003).

### BR-003: Pace

Pace is the elapsed session time divided by the distance, shown in minutes and seconds per 100 m, rounded down to whole seconds.

### BR-004: Tile Colour

Tile colour runs from green right after a change to red once the seconds since the last change reach the participant's pace value.

## Notes

- There is no lower limit on the lap count, so repeated corrections can make it negative.
- Laps can be counted while the session clock is not running.
