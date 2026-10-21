# UC-002: Run Session Clock

## Overview

- **ID:** UC-002
- **Name:** Run Session Clock
- **Primary Actor:** Timekeeper
- **Goal:** Measure the elapsed time of the session so distances can be turned into a pace.
- **Trigger:** Timekeeper chooses to start, stop or continue the session clock.
- **Status:** Draft

## Preconditions

- The participant editor is closed (UC-001 completed at least once in this session).

## Main Success Scenario

1. Timekeeper starts the session clock.
2. System records the start time and shows the elapsed time, updated every second.
3. Timekeeper stops the session clock when the session ends.
4. System records the stop time and freezes the displayed elapsed time.

## Alternative Flows

### A1: Timekeeper continues a stopped clock (after step 4)

1. Timekeeper chooses to continue the clock.
2. System sets the clock running again from the original start time, so the elapsed time includes the time it was stopped.
3. Use case continues at step 3.

## Postconditions

### Success

- The clock state (start, stop time, running or stopped) is stored in the browser and survives a page reload.

### Failure

- _None — starting, stopping and continuing always succeed._

## Business Rules

- **BR-001:** Elapsed time is measured from the moment the clock was first started until now (running) or until the last stop (stopped).
- **BR-002:** The elapsed time is shown as hours, minutes and seconds.
- **BR-003:** A clock that was never started shows zero elapsed time.

> **Note:** Continuing does not pause-and-resume; it resumes as if the clock had never stopped. This may be unintended.
