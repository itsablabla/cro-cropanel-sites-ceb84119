# Qualification language vague — dev spec
Site: nomadinternet.com · Priority 2 · Medium · Effort: Medium (2-5 days)

## Problem
CTAs ask to check coverage but do not explain what qualification means, leaving visitors uncertain.

## Evidence (from the live site)
> 7 distinct calls to action compete on the same page: “CHECK COVERAGE”, “CHECK IF IT WORKS AT MY ADDRESS”, “SEE MY OPTIONS”, “GET STARTED”, “START CHAT”, “SEE WHAT I QUALIFY FOR”, “CHECK MY COVERAGE”.
> A section heading reads “You qualify for everything”.

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: No explanation of qualification criteria.

## Required change
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Add explanatory sentence near CTAs.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add explanatory sentence near CTAs.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_qualification_language_vague` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
