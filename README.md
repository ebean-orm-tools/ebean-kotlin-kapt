# ebean-enhancement tile

Maven tile that performs the Ebean Kotlin query bean generation using KAPT.

## Example use

In your project pom under build / plugins add the tiles-maven-plugin with the following configuration. Note that this example also brings in the java-compile tile.

```xml
      <!-- maven build / plugins -->

      <plugin>
        <groupId>io.repaint.maven</groupId>
        <artifactId>tiles-maven-plugin</artifactId>
        <version>2.8</version>
        <extensions>true</extensions>
        <configuration>
          <tiles>
            <tile>io.ebean.tile:kotlin-kapt:1.1</tile>
            <tile>io.ebean.tile:enhancement:2.8</tile>
          </tiles>
        </configuration>
      </plugin>

```



## What it does


```xml

  <!-- defaults, override in your project pom if needed -->

  <properties>
    <kotlin.version>1.1.3-2</kotlin.version>
    <kotlin.compiler.jvmTarget>1.8</kotlin.compiler.jvmTarget>
    <kotlin-querybean-generator.version>10.1.2</kotlin-querybean-generator.version>
  </properties>

  <!-- brought into build / plugins -->

  <build>

    <sourceDirectory>${project.basedir}/src/main/kotlin</sourceDirectory>
    <testSourceDirectory>${project.basedir}/src/test/kotlin</testSourceDirectory>

    <plugins>

      <plugin>
        <groupId>io.ebean.tools</groupId>
        <artifactId>codegen-maven-plugin</artifactId>
        <version>${codegen-maven-plugin.version}</version>
      </plugin>

      <plugin>
        <artifactId>kotlin-maven-plugin</artifactId>
        <groupId>org.jetbrains.kotlin</groupId>
        <version>${kotlin.version}</version>
        <executions>
          <execution>
            <id>kapt</id>
            <goals>
              <goal>kapt</goal>
            </goals>
            <configuration>
              <sourceDirs>
                <sourceDir>src/main/kotlin</sourceDir>
              </sourceDirs>
              <annotationProcessorPaths>
                <annotationProcessorPath>
                  <groupId>io.ebean</groupId>
                  <artifactId>kotlin-querybean-generator</artifactId>
                  <version>${kotlin-querybean-generator.version}</version>
                </annotationProcessorPath>
              </annotationProcessorPaths>
            </configuration>
          </execution>

          <execution>
            <id>compile</id>
            <goals>
              <goal>compile</goal>
            </goals>
            <configuration>
              <sourceDirs>
                <sourceDir>src/main/kotlin</sourceDir>
              </sourceDirs>
            </configuration>
          </execution>

          <execution>
            <id>test-compile</id>
            <goals>
              <goal>test-compile</goal>
            </goals>
            <configuration>
              <sourceDirs>
                <sourceDir>src/test/kotlin</sourceDir>
              </sourceDirs>
            </configuration>
          </execution>

        </executions>
      </plugin>
    </plugins>

  </build>

```
