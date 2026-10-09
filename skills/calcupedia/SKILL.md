---
name: calcupedia
description: Run exact calculations and unit conversions with Calcupedia's 2,400+ calculators (mortgage, loans, tax, salary, BMI, calories, concrete, physics, unit conversion and more). Use when someone needs a precise number from a known formula, wants to compare scenarios, or wants a calculator to embed on a website.
---

# Calcupedia

Calcupedia's MCP tools run real calculators with verified formulas, so results are exact and repeatable instead of estimated.

## When to use it

- The person asks for a number that comes from a standard formula: loan or mortgage payments, interest, tax, salary and take-home pay, BMI, calories, construction quantities, physics, unit conversions.
- The person wants to try different values ("what if the rate is 7%?"). In Claude, the calculator card lets them change inputs themselves.
- The person wants a calculator on their own website: use `get_embed_link`.

## How to use it

1. Call `search_calculators` with a few keywords (for example "mortgage", "bmi", "kg to lbs"). The top results list each calculator's input keys, defaults and allowed values.
2. Call `run_calculator` once, with the calculator's slug and the person's values, using those input keys. Leave out inputs the person didn't give; the calculator uses its defaults.
3. Report the main result, mention any defaults you relied on, and share the link the tool returns so the person can open the calculator with their values.

## Notes

- Results are for general information, not financial, medical or legal advice.
- Calcupedia (calcupedia.io) is not related to the Casio calculator wiki of the same name.
