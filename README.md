# dangernoodle-io-build-pom

[![maven-central](https://img.shields.io/maven-central/v/io.dangernoodle/dangernoodle-io-build-pom.svg)](https://img.shields.io/maven-central/v/io.dangernoodle/dangernoodle-io-build-pom.svg)
[![maven-build](https://github.com/dangernoodle-io/dangernoodle-io-build-pom/actions/workflows/maven-build.yml/badge.svg)](https://github.com/dangernoodle-io/dangernoodle-io-build-pom/actions/workflows/maven-build.yml)
[![maven-release](https://github.com/dangernoodle-io/dangernoodle-io-build-pom/actions/workflows/maven-release.yml/badge.svg)](https://github.com/dangernoodle-io/dangernoodle-io-build-pom/actions/workflows/maven-release.yml)

dangernoodle.io organization build pom

```xml
  <parent>
    <groupId>io.dangernoodle</groupId>
    <artifactId>dangernoodle-io-build-pom</artifactId>
    <version>X.Y.Z</version>
    <relativePath />
  </parent>
```

### Code Coverage

Add the following to the downstream maven `pom.xml`

```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.jacoco</groupId>
        <artifactId>jacoco-maven-plugin</artifactId>
      </plugin>
      <plugin>
        <groupId>com.github.hazendaz.maven</groupId>
        <artifactId>coveralls-maven-plugin</artifactId>
      </plugin>
    </plugins>
  </build>
```
