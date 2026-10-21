# Use Case: Prepare Session

## Overview

**Use Case ID:** UC-001  
**Use Case Name:** Prepare Session  
**Primary Actor:** Timekeeper  
**Goal:** Define who takes part in the session and how long one lap is, so laps can be counted per participant.  
**Trigger:** Timekeeper asks to edit the participant list.  
**Status:** Draft  

## Preconditions

- The Lap Counter is open in the Timekeeper's browser.

## Main Success Scenario

1. Timekeeper asks to edit the participant list.
2. System shows the current participant names, one per line, and the lap length options.
3. Timekeeper enters or changes the participant names, separated by commas and/or line breaks.
4. Timekeeper selects the lap length.
5. Timekeeper confirms the participant list.
6. System cleans up the list by trimming names and dropping empty entries, and sorts it alphabetically.
7. System saves the participant list and lap length and closes the editor.
8. System shows one tile per participant, ready for lap counting.

## Alternative Flows

### A1: Participant Removed from the List

**Trigger:** A participant that already has counted laps is no longer in the confirmed list (step 6)  
**Flow:**

1. System removes the participant's tile but keeps the counted laps.
2. Use case continues at step 7.

### A2: Same Name Entered Twice

**Trigger:** The Timekeeper entered a name more than once (step 6)  
**Flow:**

1. System keeps both entries; both tiles show and change the same lap count.
2. Use case continues at step 7.

## Postconditions

### Success Postconditions

- The participant list and lap length are stored in the browser and survive a page reload.
- Every other open Lap Counter tab in the same browser shows the updated list.

### Failure Postconditions

- The stored participant list is unchanged while the editor is still open.

## Business Rules

### BR-001: Name Entry

Participant names are separated by commas or line breaks; surrounding spaces are ignored and empty names are dropped.

### BR-002: Alphabetical Order

The participant list is always shown in alphabetical order.

### BR-003: Lap Length

The lap length is one of 16 m, 25 m, 33 m, 50 m, 100 m or 200 m; the default is 50 m.

### BR-004: Laps Tied to Name

Lap counts are kept per participant name. A name that is removed and later added again with the same spelling gets its earlier lap count back.

## Notes

- The lap length selector is not restored from storage: after a page reload the selector and the stored lap length go back to 50 m, even if another length was chosen before.
- The editor is open on first use and after a reset (UC-005).
