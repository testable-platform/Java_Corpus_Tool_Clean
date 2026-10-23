# CK

Synthetic, clean-by-design Java project for **CK**.

Domain: trail routing (TrailRouter) -- static OO metrics target

**Not installed here**: see Notes for why, and what was checked instead.

## What a passing result looks like

CK's per-class/per-method static metrics (WMC, CBO, LCOM, RFC) would read low across TrailRouter, which is deliberately kept to small, single-purpose methods with few fields and little cross-class coupling.

## Command

```bash
java -jar ck.jar <src> false 0 false <out>
```

## Notes

CK 0.7.0 depends on JavaParser (`com.github.javaparser:javaparser-core`), which is not reachable via Maven Central here, and CK's own release jar is a GitHub Release asset -- both channels return 403 at this sandbox's egress proxy. TrailRouter's source is written clean regardless.

## Per-family results

Boundary families this tool was exploded into, and what each one's own real invocation found (not asserted -- see `_generator/verify_live.py`):

| Family | Host JDK | Result |
|---|---|---|
| `java16` | JDK 17 host, `--release 16` | NOT INSTALLED |


CK 0.7.0 needs JavaParser, resolved from Maven Central, which is blocked at this sandbox's egress proxy; CK's own release jar is a GitHub Release asset too. No JDK family changes this.

This repo carries only the `java16` family.
