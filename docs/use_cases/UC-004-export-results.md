# UC-004: Export Results

## Overview

- **ID:** UC-004
- **Name:** Export Results
- **Primary Actor:** Timekeeper
- **Goal:** Take the session results out of the app as a spreadsheet file for keeping or further analysis.
- **Trigger:** Timekeeper chooses to export the results.
- **Status:** Draft

## Preconditions

- The Lap Counter is open in the Timekeeper's browser.

## Main Success Scenario

1. Timekeeper chooses to export the results.
2. System determines the elapsed session time (UC-002 BR-001).
3. System builds one result row per participant on the list with name, laps, time in seconds, distance in metres and split in seconds per 100 m.
4. System offers the results to the Timekeeper as a file named `laps.csv`.
5. Timekeeper saves the file.

## Alternative Flows

### A1: Clock never started (at step 2)

1. The session clock was never started.
2. System uses an elapsed time of zero.
3. Use case continues at step 3.

## Postconditions

### Success

- The Timekeeper has a comma-separated file with a header row and one row per participant.
- The stored session data is unchanged.

### Failure

- The stored session data is unchanged.

## Business Rules

- **BR-001:** The export holds exactly the participants currently on the list, in list order; laps kept for removed participants are not exported.
- **BR-002:** The time column is the same elapsed session time for every participant.
- **BR-003:** Split is the elapsed time divided by the participant's distance, expressed per 100 m and not rounded.

> **Note:** For a participant with no laps the split column holds a non-numeric value, since the code divides by a zero distance.
