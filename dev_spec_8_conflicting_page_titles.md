# Conflicting page titles — dev spec
Site: nomadinternet.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
The page title misleads visitors about content, breaking navigation scent.

## Evidence (from the live site)
> The browser title reads “How Nomad Internet Works - YouTube”.
> The page's main headline reads “Let's Get You the Right Internet”.

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Title says YouTube, content is rural internet.

## Required change
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Update title to accurately describe content.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Update title to accurately describe content.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_conflicting_page_titles` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
