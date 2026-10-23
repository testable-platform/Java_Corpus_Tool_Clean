# sonar

Synthetic, clean-by-design Java project for **SonarQube / SonarScanner**.

Domain: tide-height table (`TideTable`).

**Not installed here**: Sonar analysis needs a running SonarQube server plus the scanner, and the scanner distribution (binaries.sonarsource.com, Maven Central) is refused by this sandbox's egress proxy (HTTP 403 on the CONNECT, measured this session). Nothing below was produced by running Sonar; see Notes.

## What a passing result looks like

The Sonar quality gate passes with no issues on TideTable: small methods, no duplicated literals, no unused members, a private constructor on the utility class, no console output, no TODO tags.

## Command

```bash
sonar-scanner -Dsonar.projectKey=sonar-clean-tidetable -Dsonar.sources=java8/src/main/java \
    -Dsonar.tests=java8/src/test/java -Dsonar.java.binaries=build/main -Dsonar.host.url=$SONAR_HOST_URL
```

Expected: quality gate passed, zero issues (not run -- see Notes)

## Layout

```text
sonar/
  README.md
  java8/ ... java25/        one folder per JDK family (18), identical source
    src/main/java/tidetable/TideTable.java
    src/test/java/tidetable/TideTableTest.java
```

## Notes

What **was** run, in every family: the source compiles with plain `javac --release N` on a JDK 25 host and the JUnit 4 tests pass, for N = 8 to 25 (18 of 18 families compile and pass). No suppression comments or annotations anywhere, so a scanner sees exactly what is there.

## Per-family results

| Family | Host JDK | Result |
|---|---|---|
| `java24` | JDK 25 host, `--release 24` | NOT INSTALLED |

Every family has the same blocker (no server, no scanner), so the column is the same for all 18. Each family's source was compiled with `javac --release N` on a JDK 25 host and its tests pass.

This repo carries only the `java24` family.
