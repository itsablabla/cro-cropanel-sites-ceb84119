# Duplicate forms create ambiguity — dev spec
Site: nomadinternet.com · Priority 4 · Urgent · Effort: Medium (2-5 days)

## Problem
Two identical CONTINUE forms on the same page create ambiguity about the intended next step.

## Evidence (from the live site)
> Two identical CONTINUE forms appear on the same pages

## Current state
h1: Let's Get You the Right Internet; cta: CONTINUE (duplicate); notes: Duplicate forms on the same page.

## Required change
h1: Let's Get You the Right Internet; cta: CONTINUE (single); notes: Render a single coverage-check form per page.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Render a single coverage-check form per page.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_forms_create_ambiguity` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
