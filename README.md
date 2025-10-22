# javadoc-toolchain-repro

Minimal reproduction for [maven-javadoc-plugin#1244](https://github.com/apache/maven-javadoc-plugin/issues/1244)

## Steps to reproduce

1. Set up [a `toolchains.xml` configuration file](https://maven.apache.org/guides/mini/guide-using-toolchains.html) on your local machine containing at least a toolchain for Java 21.
2. Run `mvn javadoc:javadoc` from the root of this repo using JDK 23 or higher.

## Expected result

The Javadoc site is produced.

## Actual result

Javadoc generation fails with the following error:

```
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-javadoc-plugin:3.12.0:javadoc (default-cli) on project javadoc-toolchain-repro: An error has occurred in Javadoc report generation:
[ERROR] Exit code: 1
[ERROR] error: invalid flag: --no-fonts
```
