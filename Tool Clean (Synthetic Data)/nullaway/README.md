# nullaway

Synthetic, clean-by-design Java project for **NullAway**.

Domain: canal-wharf berth register (`BargeBerth`).

**Not installed here**: NullAway is not a standalone program. It is an Error Prone compiler plugin, resolved from Maven Central, which this sandbox's egress proxy refuses (HTTP 403 on the CONNECT, measured this session). Nothing below was produced by running NullAway or Error Prone; see Notes.

## What a passing result looks like

NullAway (annotated package `bargeberth`) reports zero errors against BargeBerth: the one method that can return null, `occupant`, is marked `@Nullable`, both callers test the result before using it, and the only field is assigned in the constructor.

## Command

```bash
javac -XDcompilePolicy=simple -processorpath <error_prone_core + nullaway jars> \
    "-Xplugin:ErrorProne -XepDisableAllChecks -Xep:NullAway:ERROR -XepOpt:NullAway:AnnotatedPackages=bargeberth" \
    -d build/main java8/src/main/java/bargeberth/*.java
```

Expected: no output, exit code 0 (not run -- see Notes)

## Layout

```text
nullaway/
  README.md
  java8/ ... java25/        one folder per JDK family (18), identical source
    src/main/java/bargeberth/BargeBerth.java
    src/main/java/bargeberth/Nullable.java   local @Nullable annotation
    src/test/java/bargeberth/BargeBerthTest.java
```

## Notes

`Nullable.java` is a local annotation with the simple name `Nullable`; NullAway matches nullness annotations by simple name, so the fixture needs no third-party annotation jar to compile.

What **was** run, in every family: the source compiles with plain `javac --release N` on a JDK 25 host and the JUnit 4 tests pass, for N = 8 to 25 (18 of 18 families compile and pass).

## Per-family results

| Family | Host JDK | Result |
|---|---|---|
| `java25` | JDK 25 (native) | NOT INSTALLED |

Every family has the same blocker (the Error Prone plugin cannot be fetched), so the column is the same for all 18. Each family's source was compiled with `javac --release N` on a JDK 25 host and its tests pass.

This repo carries only the `java25` family.
