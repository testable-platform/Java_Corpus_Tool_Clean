# Testable Java corpus — JV_V8_MAVEN_THINJAR_MICRO

Grid cell `MVN-THIN-S` of the 24-cell Java grid.

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
| Java version | 8 |
| Host JDK | 8 |
| Build system | Maven |
| Packaging | Thin jar |
| Architecture | Microservices |

## Build

```
mvn -B clean package
```

Main and test sources both compile at Java 8 (bytecode major version 52). The code
uses lambdas, method references, streams, `Optional`, `java.time` and default interface
methods, so it fails to compile under `-source 7` — the version differentiation is real,
not declared.

Produces: `dist/jv-002.jar or target/jv-002-1.0.0.jar`

## Run

```
java -jar <artifact> O-1234
```

## Test

```
mvn -B test
```

## Workspace projects

- `jv-002-domain/`
- `jv-002-pricing/`
- `jv-002-risk/`
- `jv-002-catalog/`


## `Tool Clean (Synthetic Data)/`
This repo carries only this branch's own `java8` family -- one of the five boundary families (`java8`, `java9`, `java16`, `java24`, `java25`) this corpus samples; see testable-platform/java-corpus for the full 18-family set.

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

