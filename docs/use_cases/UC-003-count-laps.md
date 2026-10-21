# UC-003: Count Laps

## Overview

- **ID:** UC-003
- **Name:** Count Laps
- **Primary Actor:** Timekeeper
- **Goal:** Keep an accurate lap count for each participant during the session and see each participant's distance and pace.
- **Trigger:** A participant completes a lap and the Timekeeper taps that participant's tile.
- **Status:** Draft

## Preconditions

- At least one participant is on the participant list (UC-001).

## Main Success Scenario

1. Participant completes a lap.
2. Timekeeper briefly taps the participant's tile.
3. System adds one lap to the participant's count and records the current elapsed session time as the time of the last lap.
4. System briefly animates the tile to confirm the tap.
5. System shows the participant's updated lap count, distance and pace per 100 m.
6. System colours the tile from green towards red as the time since the participant's last lap grows.

## Alternative Flows

### A1: Timekeeper corrects a miscounted lap (at step 2)

1. Timekeeper presses and holds the participant's tile for at least half a second.
2. System subtracts one lap from the participant's count and records the current elapsed session time.
3. Use case continues at step 4.

### A2: Press is cancelled (at step 2)

1. The pointer moves or the touch is cancelled before the press ends.
2. System leaves the lap count unchanged.
3. The use case ends.

### A3: Participant has no distance yet (at step 5)

1. The participant's distance is zero.
2. System shows the distance as 0 m and leaves the pace blank.
3. Use case continues at step 6.

## Postconditions

### Success

- The participant's lap count and time of last lap are stored in the browser and survive a page reload.
- Every other open tab of the Lap Counter in the same browser shows the updated count.

### Failure

- The participant's lap count is unchanged.

## Business Rules

- **BR-001:** A short press adds one lap; a press held for 500 ms or longer removes one lap.
- **BR-002:** Distance equals the lap count times the lap length (UC-001 BR-003).
- **BR-003:** Pace is the elapsed session time divided by the distance, shown in minutes and seconds per 100 m, rounded down to whole seconds.
- **BR-004:** Tile colour runs from green (lap just counted) to red once the seconds since the last lap reach the participant's pace value.

> **Note:** The code puts no lower limit on the lap count, so repeated corrections can make it negative. Laps can also be counted while the clock is not running.
