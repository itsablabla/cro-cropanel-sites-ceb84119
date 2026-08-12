# Competing CTAs split funnel — dev spec
Site: nomadinternet.com · Priority 3 · Urgent · Effort: Low (0.5-2 days)

## Problem
Multiple competing CTAs fragment the primary path, creating ambiguity about which action advances the user.

## Evidence (from the live site)
> CHECK COVERAGE | CHECK IF IT WORKS AT MY ADDRESS | SEE MY OPTIONS | GET STARTED | START CHAT | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE, CHECK IF IT WORKS AT MY ADDRESS, SEE MY OPTIONS, GET STARTED, START CHAT, SEE WHAT I QUALIFY FOR, CHECK MY COVERAGE; notes: Multiple CTAs all appear to lead to the same coverage check.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE (primary), de-emphasize secondary CTAs; notes: Consolidate coverage-check CTAs into one consistent primary action label.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate coverage-check CTAs into one consistent primary action label.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_competing_ctas_split_funnel` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
