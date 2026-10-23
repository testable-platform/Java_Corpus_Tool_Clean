# OWASP Dependency-Check

Synthetic, clean-by-design Java project for **OWASP Dependency-Check**.

Domain: grain-intake dependency ledger (GrainIntake)

**Not installed here**: see Notes for why, and what was checked instead.

## What a passing result looks like

A Dependency-Check scan of GrainIntake's pinned dependencies would report zero CVE matches against the NVD database, all pins chosen from current releases with no disclosed vulnerabilities.

## Command

```bash
dependency-check.sh --project GrainIntake --scan .
```

## Notes

Dependency-Check ships as a GitHub Release zip or a Maven/Gradle plugin resolved from Maven Central; both are blocked at this sandbox's egress proxy (measured: 403 on both hosts), and there is no Debian package for it.

## Per-family results

Boundary families this tool was exploded into, and what each one's own real invocation found (not asserted -- see `_generator/verify_live.py`):

| Family | Host JDK | Result |
|---|---|---|
| `java8` | JDK 8 (native) | NOT INSTALLED |


Ships as a GitHub Release zip or a Maven/Gradle plugin, both blocked at the egress proxy; no Debian package exists. No JDK family changes this.

This repo carries only the `java8` family.
