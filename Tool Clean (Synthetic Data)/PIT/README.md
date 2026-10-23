# PIT

Synthetic, clean-by-design Java project for **PIT**.

Domain: stone-grading quarry logic (StoneGrader)

**Not installed here**: see Notes for why, and what was checked instead.

## What a passing result looks like

PIT mutation testing on StoneGrader would report a 100% mutation score -- every mutant PIT's operators can generate in the grading logic is killed by the JUnit4 suite.

## Command

```bash
mvn org.pitest:pitest-maven:mutationCoverage
```

## Notes

PIT is distributed purely through Maven Central / the Gradle Plugin Portal, both blocked at this sandbox's egress proxy (measured: 403 on `repo1.maven.org` and `plugins.gradle.org`). No apt package exists.

## Per-family results

Boundary families this tool was exploded into, and what each one's own real invocation found (not asserted -- see `_generator/verify_live.py`):

| Family | Host JDK | Result |
|---|---|---|
| `java16` | JDK 17 host, `--release 16` | NOT INSTALLED |


Distributed purely through Maven Central / the Gradle Plugin Portal, both blocked at the egress proxy; no apt package exists. No JDK family changes this.

This repo carries only the `java16` family.
