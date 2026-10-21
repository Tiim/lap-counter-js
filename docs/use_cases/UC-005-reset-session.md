# Use Case: Reset Session

## Overview

**Use Case ID:** UC-005  
**Use Case Name:** Reset Session  
**Primary Actor:** Timekeeper  
**Goal:** Clear everything from the previous session to start a new one from scratch.  
**Trigger:** Timekeeper asks to reset the session.  
**Status:** Draft  

## Preconditions

- The participant editor is open.

## Main Success Scenario

1. Timekeeper asks to reset the session.
2. System clears all lap counts.
3. System clears the participant list and empties the editor.
4. System clears the session clock and sets the stored lap length back to 50 m.
5. System keeps the participant editor open, ready for a new session.

## Alternative Flows

_None — the reset happens without confirmation and has no other branch._

## Postconditions

### Success Postconditions

- No participants, lap counts or clock state remain in the browser.
- Every other open Lap Counter tab in the same browser shows the empty session.

### Failure Postconditions

_None — the reset has no failing branch._

## Business Rules

### BR-001: Irreversible Reset

A reset removes all session data at once and cannot be undone.

### BR-002: Reset Availability

Reset is only offered while the participant editor is open.

## Notes

- After a reset the lap length selector keeps showing the previously chosen length while the stored lap length is 50 m.
