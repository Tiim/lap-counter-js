# Use Case: Run Session Clock

## Overview

**Use Case ID:** UC-002  
**Use Case Name:** Run Session Clock  
**Primary Actor:** Timekeeper  
**Goal:** Measure the elapsed time of the session so that distances can be turned into a pace.  
**Trigger:** Timekeeper starts the session clock.  
**Status:** Draft  

## Preconditions

- The participant editor is closed.

## Main Success Scenario

1. Timekeeper starts the session clock.
2. System records the start time and shows the elapsed time, updated every second.
3. Timekeeper stops the session clock when the session ends.
4. System records the stop time and freezes the displayed elapsed time.

## Alternative Flows

### A1: Continue a Stopped Clock

**Trigger:** Timekeeper continues the clock after stopping it (step 4)  
**Flow:**

1. System sets the clock running again from the original start time, so the elapsed time includes the time it was stopped.
2. Use case continues at step 3.

## Postconditions

### Success Postconditions

- The clock state (start time, stop time, running or stopped) is stored in the browser and survives a page reload.

### Failure Postconditions

_None — starting, stopping and continuing the clock have no failing branch._

## Business Rules

### BR-001: Elapsed Time

Elapsed time runs from the moment the clock was first started until now while it runs, or until the last stop while it is stopped.

### BR-002: Time Display

The elapsed time is shown as hours, minutes and seconds.

### BR-003: Clock Not Started

A clock that was never started shows zero elapsed time.

## Notes

- Continuing does not resume a paused clock; it carries on as if the clock had never stopped. This may be unintended.
