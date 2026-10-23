# Testable Java corpus — JV_V9_GRADLEKOTLINDSL_THINJAR_MICRO

Grid cell `GRK-THIN-S` of the 24-cell Java grid.

## Project type

Order pricing and risk domain. The domain layer is byte-identical across all 24 branches
in this family, so any difference in tool output is attributable to the branch variables
below and not to the code the tool was pointed at.

## Branches

This repository holds 432 orphan branches, one per grid cell across every Java version, build system and packaging combination in this corpus. `main` carries the title
only. See `dataset.json` for the machine-readable description of this branch.

## Branch variables

| Variable | Value |
|---|---|
| Java version | 9 |
| Host JDK | 11 |
| Build system | Gradle / Kotlin DSL |
| Packaging | Thin jar |
| Architecture | Microservices |

## Build

```
./gradlew build
```

Main and test sources both compile at Java 9 (bytecode major version 53). The code
uses private interface methods, `Set.of`, `Optional.or`, `Optional.stream`,
`Stream.takeWhile`, try-with-resources on an effectively-final variable and the diamond
operator on an anonymous class, so it fails to compile under `--release 8` — the version differentiation is real, not
declared.

Produces: `dist/jv-128.jar or target/jv-128-1.0.0.jar`

## Run

```
java -jar <artifact> O-1234
```

## Test

```
./gradlew test
```

## Workspace projects

- `jv-128-domain/`
- `jv-128-pricing/`
- `jv-128-risk/`
- `jv-128-catalog/`


## `Tool Clean (Synthetic Data)/`
This repo carries only this branch's own `java9` family -- one of the five boundary families (`java8`, `java9`, `java16`, `java24`, `java25`) this corpus samples; see testable-platform/java-corpus for the full 18-family set.

## Planted CVE pins

| Dependency | Version |
|---|---|
| `commons-collections:commons-collections` | 3.2.1 |
| `org.apache.commons:commons-text` | 1.9 |
| `com.fasterxml.jackson.core:jackson-databind` | 2.9.10.1 |
| `log4j:log4j` | 1.2.17 |
| `org.yaml:snakeyaml` | 1.30 |

Deliberately vulnerable versions, so the SCA metrics have known true positives. Do not
upgrade them.

