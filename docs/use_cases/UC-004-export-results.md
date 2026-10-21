# Use Case: Export Results

## Overview

**Use Case ID:** UC-004  
**Use Case Name:** Export Results  
**Primary Actor:** Timekeeper  
**Goal:** Take the session results out of the app as a spreadsheet file for keeping or further analysis.  
**Trigger:** Timekeeper asks to export the results.  
**Status:** Draft  

## Preconditions

- The Lap Counter is open in the Timekeeper's browser.

## Main Success Scenario

1. Timekeeper asks to export the results.
2. System determines the elapsed session time (UC-002 BR-001).
3. System builds one result row per participant on the list with name, laps, time in seconds, distance in metres and split in seconds per 100 m.
4. System offers the results as a comma-separated file named laps.csv.
5. Timekeeper saves the file.

## Alternative Flows

### A1: Clock Never Started

**Trigger:** The session clock was never started (step 2)  
**Flow:**

1. System uses an elapsed time of zero.
2. Use case continues at step 3.

## Postconditions

### Success Postconditions

- The Timekeeper has a comma-separated file with a header row and one row per participant.
- The stored session data is unchanged.

### Failure Postconditions

- The stored session data is unchanged.

## Business Rules

### BR-001: Exported Participants

The export holds exactly the participants currently on the list, in list order; laps kept for removed participants are not exported.

### BR-002: Common Time

The time column holds the same elapsed session time for every participant.

### BR-003: Split

Split is the elapsed time divided by the participant's distance, expressed per 100 m and not rounded.

## Notes

- For a participant with no laps the split column holds a non-numeric value, since the distance is zero.
