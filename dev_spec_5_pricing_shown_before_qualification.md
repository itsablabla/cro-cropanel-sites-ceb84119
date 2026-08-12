# Pricing shown before qualification — dev spec
Site: nomadinternet.com · Priority 5 · High · Effort: Medium (2-5 days)

## Problem
Prices displayed before coverage qualification cause users to self-select out based on sticker price.

## Evidence (from the live site)
> Prices shown on the page: $99.95/month $129.95/month $99.95/Mo $99.95/month $129.95/month $99.95
> A section heading reads “$99.95 /month”.
> A section heading reads “$129.95 /month”.

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Prices shown before coverage check.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Move pricing display to after coverage qualification.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Move pricing display to after coverage qualification.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_pricing_shown_before_qualification` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
