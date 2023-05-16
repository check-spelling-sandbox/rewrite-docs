# Parameterize Log4j 2.x logging statements

**org.openrewrite.java.logging.log4j.ParameterizedLogging**

_Log4j 2.x supports parameterized logging, which can significantly boost logging performance for disabled logging statements._

### Tags

* logging
* log4j

## Source

[GitHub](https://github.com/openrewrite/rewrite-logging-frameworks/blob/main/src/main/resources/META-INF/rewrite/log4j.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-logging-frameworks/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-logging-frameworks/1.20.1/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-logging-frameworks
* version: 1.20.1

## Contributors
* [Aaron Gershman](5619476+aegershman@users.noreply.github.com)
* [Patrick](patway99@gmail.com)
* [Jonathan Schneider](jkschneider@gmail.com)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-logging-frameworks:1.20.1` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.logging.log4j.ParameterizedLogging")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-logging-frameworks:1.20.1")
}
```
{% endcode %}
{% endtab %}
{% tab title="Maven POM" %}
{% code title="pom.xml" %}
```markup
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>4.45.0</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.java.logging.log4j.ParameterizedLogging</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-logging-frameworks</artifactId>
            <version>1.20.1</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-logging-frameworks:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.logging.log4j.ParameterizedLogging
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Logger info(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Logger trace(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Logger debug(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Logger info(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Logger warn(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Logger error(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Logger fatal(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Category info(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Logger trace(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Category debug(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Category info(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Category warn(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Category error(..)`
* [Parameterize logging statements](../../../java/logging/parameterizedlogging.md)
  * methodPattern: `org.apache.logging.log4j.Category fatal(..)`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.logging.log4j.ParameterizedLogging
displayName: Parameterize Log4j 2.x logging statements
description: Log4j 2.x supports parameterized logging, which can significantly boost logging performance for disabled logging statements.
tags:
  - logging
  - log4j
recipeList:
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Logger info(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Logger trace(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Logger debug(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Logger info(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Logger warn(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Logger error(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Logger fatal(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Category info(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Logger trace(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Category debug(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Category info(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Category warn(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Category error(..)
  - org.openrewrite.java.logging.ParameterizedLogging:
      methodPattern: org.apache.logging.log4j.Category fatal(..)

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.logging.log4j.ParameterizedLogging)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
