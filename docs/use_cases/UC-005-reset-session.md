# UC-005: Reset Session

## Overview

- **ID:** UC-005
- **Name:** Reset Session
- **Primary Actor:** Timekeeper
- **Goal:** Clear everything from the previous session to start a new one from scratch.
- **Trigger:** Timekeeper chooses to reset while the participant editor is open.
- **Status:** Draft

## Preconditions

- The participant editor is open (UC-001).

## Main Success Scenario

1. Timekeeper chooses to reset.
2. System clears all lap counts.
3. System clears the participant list and empties the editor.
4. System clears the session clock and sets the lap length back to 50 m.
5. System keeps the participant editor open, ready for a new session (UC-001).

## Alternative Flows

_None — the code resets without asking for confirmation and has no other branch._

## Postconditions

### Success

- No participants, lap counts or clock state remain in the browser storage.
- Every other open tab of the Lap Counter in the same browser shows the empty session.

### Failure

- _None — the reset has no failing branch._

## Business Rules

- **BR-001:** A reset removes all session data at once and cannot be undone.
- **BR-002:** Reset is only offered while the participant editor is open.

> **Note:** After a reset the lap length selector keeps showing the previously chosen length while the stored lap length is 50 m.
