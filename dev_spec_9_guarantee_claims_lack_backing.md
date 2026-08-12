# Guarantee claims lack backing — dev spec
Site: nomadinternet.com · Priority 9 · Medium · Effort: Low (0.5-2 days)

## Problem
The 'SHOP WITH CONFIDENCE' claim lacks visible guarantee details, undermining trust.

## Evidence (from the live site)
> A section heading reads “SHOP WITH CONFIDENCE”.
> A section heading reads “Real Stories from Real Users”.
> A section heading reads “Why Nomad?”.

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: No guarantee details visible.

## Required change
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Add explicit guarantee terms under heading.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add explicit guarantee terms under heading.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_guarantee_claims_lack_backing` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
