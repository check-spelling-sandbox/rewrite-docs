# Find patterns that require updating for Spring Boot 2.5

**org.openrewrite.java.spring.boot2.search.FindUpgradeRequirementsSpringBoot\_2\_5**

_Looks for a series of patterns that have not yet had auto-remediation recipes developed for._

### Tags

* spring
* boot

## Source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-boot-25.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/4.36.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 4.36.0

## Contributors
* [Fabian Krüger](56278322+fabapp2@users.noreply.github.com)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Alex Boyko](aboyko@pivotal.io)
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)
* [Nick McKinney](mckinneynichoals@gmail.com)
* [Kyle Scully](scullykns@gmail.com)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-spring:4.36.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.spring.boot2.search.FindUpgradeRequirementsSpringBoot_2_5")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-spring:4.36.0")
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
            <recipe>org.openrewrite.java.spring.boot2.search.FindUpgradeRequirementsSpringBoot_2_5</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>4.36.0</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.spring.boot2.search.FindUpgradeRequirementsSpringBoot_2_5
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Find projects affected by changes to the default error view message attribute](../../../../java/spring/boot2/search/messagesinthedefaulterrorview.md)
* [In Spring Boot 2.5 a `DefaultConfigurationCustomizer` can now be used in favour of defining one or more `*Provider` beans](../../../../java/spring/boot2/search/customizingjooqdefaultconfiguration.md)
* [Applications using logging shutdown hooks](../../../../java/spring/boot2/search/loggingshutdownhooks.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.boot2.search.FindUpgradeRequirementsSpringBoot_2_5
displayName: Find patterns that require updating for Spring Boot 2.5
description: Looks for a series of patterns that have not yet had auto-remediation recipes developed for.

tags:
  - spring
  - boot
recipeList:
  - org.openrewrite.java.spring.boot2.search.MessagesInTheDefaultErrorView
  - org.openrewrite.java.spring.boot2.search.CustomizingJooqDefaultConfiguration
  - org.openrewrite.java.spring.boot2.search.LoggingShutdownHooks

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.spring.boot2.search.FindUpgradeRequirementsSpringBoot_2_5)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
