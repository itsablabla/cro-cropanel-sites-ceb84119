# Repeated identical headings — dev spec
Site: nomadinternet.com · Priority 7 · Medium · Effort: Low (0.5-2 days)

## Problem
Identical h1 headings across pages provide no distinct navigation cues.

## Evidence (from the live site)
> The page's main headline reads “Let's Get You the Right Internet”.
> The page's main headline reads “What Best Describes Your Time on the Road?”.
> The page's main headline reads “How Do You Use the Internet at Home?”.

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Same h1 on multiple pages.

## Required change
h1: Unique descriptive h1 per page; cta: CHECK COVERAGE; notes: Give each page a unique h1.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Give each page a unique h1.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_repeated_identical_headings` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
