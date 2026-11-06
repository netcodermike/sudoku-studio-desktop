# Validation

Authoring date: November 6, 2026. Host: Windows. Target: Windows, macOS, Linux desktop.

## Local result

Target-platform source CI is recorded after publication. This host has Python, Node.js, and .NET; other native toolchains are verified through CI. No unobserved GUI/device behavior is claimed.

## Reproducible checks

The GitHub Actions workflow builds/runs the following on `ubuntu-latest`:

```sh
javac -d build src/App.java
java -cp build App --self-test
```

## Manual acceptance

Generate a puzzle, enter a conflicting digit and check it, correct the digit, reveal the solution, and generate another puzzle. Also test malformed inputs and an unwritable output destination.

A workflow file is not evidence of a passing run. Observed CI run links and source commits are recorded after publication. Native GUI, sound, sleep/resume, and platform permissions require direct target-platform acceptance even when model tests pass.
