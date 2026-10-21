# UC-001: Prepare Session

## Overview

- **ID:** UC-001
- **Name:** Prepare Session
- **Primary Actor:** Timekeeper
- **Goal:** Define who takes part in the session and how long one lap is, so laps can be counted per participant.
- **Trigger:** Timekeeper opens the participant editor (it is open on first use and after a reset) or chooses to edit the participant list.
- **Status:** Draft

## Preconditions

- The Lap Counter is open in the Timekeeper's browser.

## Main Success Scenario

1. Timekeeper opens the participant editor.
2. System shows the current participant names, one per line, and the lap length options.
3. Timekeeper enters or changes the participant names, separated by commas and/or line breaks.
4. Timekeeper selects the lap length.
5. Timekeeper confirms the participant list.
6. System cleans up the list (trims names, drops empty entries) and sorts it alphabetically.
7. System saves the participant list and lap length and closes the editor.
8. System shows one tile per participant, ready for lap counting.

## Alternative Flows

### A1: Participant removed from the list (at step 6)

1. A participant that already has counted laps is no longer in the list.
2. System removes the participant's tile but keeps the counted laps in storage.
3. If a participant with the same name is added again later, the earlier lap count reappears.
4. Use case continues at step 7.

### A2: Same name entered twice (at step 6)

1. Timekeeper entered a name more than once.
2. System keeps both entries; both tiles show and change the same lap count.
3. Use case continues at step 7.

## Postconditions

### Success

- The participant list and lap length are stored in the browser and survive a page reload.
- Every other open tab of the Lap Counter in the same browser shows the updated list.

### Failure

- No participant list is changed while the editor is still open.

## Business Rules

- **BR-001:** Participant names are separated by commas or line breaks; surrounding spaces are ignored and empty names are dropped.
- **BR-002:** The participant list is always shown in alphabetical order.
- **BR-003:** The lap length is one of 16 m, 25 m, 33 m, 50 m, 100 m or 200 m; the default is 50 m.
- **BR-004:** Lap counts are kept per participant name, so a participant's laps are tied to the exact spelling of the name.

> **Note:** The lap length selector is not reloaded from storage: after a page reload or a reset the selector and the stored lap length start at 50 m again, even if another length was chosen before.
