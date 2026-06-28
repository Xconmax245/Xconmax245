# Contributing to Xconmax245 Profile Repository

This repository is the source for my GitHub profile. It's maintained as a first-class engineering project.

## What you can contribute

- **Bug fixes** — broken links, incorrect SVG paths, workflow errors
- **SVG improvements** — better animations, accessibility improvements, performance
- **Workflow improvements** — more efficient or reliable GitHub Actions

## What you should not contribute

- New sections, badges, or widgets without prior discussion
- Design changes without an issue first
- Third-party tracking scripts or services

## Process

1. Open an issue describing the problem or improvement
2. Fork the repository
3. Make your change in a descriptive branch (`fix/broken-footer-link`, `improve/metrics-animation`)
4. Open a pull request referencing the issue

## SVG Guidelines

- All SVGs must pass `xmllint --noout` validation
- Animations must use CSS `@keyframes` or SMIL — no JavaScript
- No external font imports — use system font stacks
- All filters must be self-contained within the SVG

## Code of Conduct

Be direct, constructive, and respectful. Engineering contributions only.
