# Migrate JUnit asserts to AssertJ

**org.openrewrite.java.testing.assertj.JUnitToAssertj**

_AssertJ provides a rich set of assertions, truly helpful error messages, improves test code readability. Converts assertions from `org.junit.jupiter.api.Assertions` to `org.assertj.core.api.Assertions`._

### Tags

* testing
* assertj

## Source

[GitHub](https://github.com/openrewrite/rewrite-testing-frameworks/blob/main/src/main/resources/META-INF/rewrite/assertj.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-testing-frameworks/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-testing-frameworks/1.37.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-testing-frameworks
* version: 1.37.0

## Contributors
* [Greg Adams](greg@moderne.io)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Patrick Way](pway99@users.noreply.github.com)
* [Sam Snyder](sam@moderne.io)
* [Patrick](patway99@gmail.com)
* [Jeroen Meijer](jjgmeijer@gmail.com)
* [Tim te Beek](timtebeek@gmail.com)
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)
* [Nick McKinney](mckinneynicholas@gmail.com)
* [Aaron Gershman](aegershman@gmail.com)
* [Jonathan Schnéider](jkschneider@gmail.com)
* [Scott Jungling](scott.jungling@gmail.com)
* [Michael Keppler](bananeweizen@gmx.de)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-testing-frameworks:1.37.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.testing.assertj.JUnitToAssertj")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-testing-frameworks:1.37.0")
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
            <recipe>org.openrewrite.java.testing.assertj.JUnitToAssertj</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-testing-frameworks</artifactId>
            <version>1.37.0</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-testing-frameworks:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.testing.assertj.JUnitToAssertj
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [JUnit `assertArrayEquals` To AssertJ](../../../java/testing/assertj/junitassertarrayequalstoassertthat.md)
* [JUnit `assertEquals` to AssertJ](../../../java/testing/assertj/junitassertequalstoassertthat.md)
* [JUnit `assertFalse` to AssertJ](../../../java/testing/assertj/junitassertfalsetoassertthat.md)
* [JUnit `assertNotEquals` to AssertJ](../../../java/testing/assertj/junitassertnotequalstoassertthat.md)
* [JUnit `assertNotNull` to AssertJ](../../../java/testing/assertj/junitassertnotnulltoassertthat.md)
* [JUnit `assertNull` to AssertJ](../../../java/testing/assertj/junitassertnulltoassertthat.md)
* [JUnit `assertSame` to AssertJ](../../../java/testing/assertj/junitassertsametoassertthat.md)
* [JUnit `assertTrue` to AssertJ](../../../java/testing/assertj/junitasserttruetoassertthat.md)
* [JUnit fail to AssertJ](../../../java/testing/assertj/junitfailtoassertjfail.md)
* [JUnit AssertThrows to AssertJ exceptionType](../../../java/testing/assertj/junitassertthrowstoassertexceptiontype.md)
* [Add Maven dependency](../../../maven/adddependency.md)
  * groupId: `org.assertj`
  * artifactId: `assertj-core`
  * version: `3.x`
  * onlyIfUsing: `org.assertj.core.api.Assertions`
  * acceptTransitive: `true`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.testing.assertj.JUnitToAssertj
displayName: Migrate JUnit asserts to AssertJ
description: AssertJ provides a rich set of assertions, truly helpful error messages, improves test code readability. Converts assertions from `org.junit.jupiter.api.Assertions` to `org.assertj.core.api.Assertions`.
tags:
  - testing
  - assertj
recipeList:
  - org.openrewrite.java.testing.assertj.JUnitAssertArrayEqualsToAssertThat
  - org.openrewrite.java.testing.assertj.JUnitAssertEqualsToAssertThat
  - org.openrewrite.java.testing.assertj.JUnitAssertFalseToAssertThat
  - org.openrewrite.java.testing.assertj.JUnitAssertNotEqualsToAssertThat
  - org.openrewrite.java.testing.assertj.JUnitAssertNotNullToAssertThat
  - org.openrewrite.java.testing.assertj.JUnitAssertNullToAssertThat
  - org.openrewrite.java.testing.assertj.JUnitAssertSameToAssertThat
  - org.openrewrite.java.testing.assertj.JUnitAssertTrueToAssertThat
  - org.openrewrite.java.testing.assertj.JUnitFailToAssertJFail
  - org.openrewrite.java.testing.assertj.JUnitAssertThrowsToAssertExceptionType
  - org.openrewrite.maven.AddDependency:
      groupId: org.assertj
      artifactId: assertj-core
      version: 3.x
      onlyIfUsing: org.assertj.core.api.Assertions
      acceptTransitive: true

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.testing.assertj.JUnitToAssertj)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
