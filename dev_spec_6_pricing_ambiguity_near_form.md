# Pricing ambiguity near form — dev spec
Site: nomadinternet.com · Priority 6 · Medium · Effort: Medium (2-5 days)

## Problem
Conflicting price points and fees near the CONTINUE form create uncertainty about commitment.

## Evidence (from the live site)
> A section heading reads “$99.95 /month”.
> A section heading reads “$129.95 /month”.
> A section heading reads “$0.00 (one-time)”.
> A section heading reads “$99.99 (one-time)”.

## Current state
h1: Let's Get You the Right Internet; cta: CONTINUE; notes: Conflicting prices and fees near form.

## Required change
h1: Let's Get You the Right Internet; cta: CONTINUE; notes: Clarify which price applies and disclose fees.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Clarify which price applies and disclose fees.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_pricing_ambiguity_near_form` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
