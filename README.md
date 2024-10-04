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
  <relativePath/>
</parent>
```

### Build Plugins

Add the following to the downstream maven `pom.xml`. Activation occurs alongside the associated profile.

##### Source and Javadocs

```xml

<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-javadoc-plugin</artifactId>
    </plugin>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-source-plugin</artifactId>
    </plugin>
  </plugins>
</build>
```

#### Surefire Tests

Mockito, Byte Buddy and others need to be explicitly added as a java agent for instrumentation. Use
the `maven-dependency-plugin` to grab it's jar location and add it to the `argLine`.

```xml

<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-dependency-plugin</artifactId>
    </plugin>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-surefire-plugin</artifactId>
      <configuration>
        <argLine>@{argLine} -javaagent:${org.mockito:mockito-core:jar}
          -javaagent:${net.bytebuddy:byte-buddy-agent:jar}
        </argLine>
      </configuration>
    </plugin>
  </plugins>
</build>
```

#### Code Coverage

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

#### Integration Tests

```xml

<build>
  <plugins>
    <plugin>
      <groupId>org.codehaus.mojo</groupId>
      <artifactId>build-helper-maven-plugin</artifactId>
    </plugin>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-failsafe-plugin</artifactId>
    </plugin>
  </plugins>
</build>
```
