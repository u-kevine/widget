# widget

A widget that shows how much of the current year is gone and how much is left.

## What it shows

- Days passed since January 1
- Days remaining until December 31
- Percentage of the year completed

## Example

```
2026 — 205 / 365 days
Days left: 160
Progress: 56.2%
[███████████░░░░░░░░░]
```

## Usage

Open `index.html` in a browser. Everything updates automatically based on your system date.

## How it works

The widget takes the current date, counts days from the start of the year, and divides by the total days in the year (366 on leap years). No dependencies, no build step.

