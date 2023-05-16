# Find uses of deprecated classes, methods, and fields

**org.openrewrite.java.search.FindDeprecatedUses**

_Find deprecated uses of methods, fields, and types. Optionally ignore those classes that are inside deprecated scopes._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/java/org/openrewrite/java/search/FindDeprecatedUses.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-java/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 7.40.6

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Sam Snyder](sam@moderne.io)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | typePattern | *Optional*. A type pattern that is used to find deprecations from certain types. |
| `Boolean` | matchInherited | *Optional*. When enabled, find types that inherit from a deprecated type. |
| `Boolean` | ignoreDeprecatedScopes | *Optional*. When a deprecated type is used in a deprecated method or class, ignore it. |


## Usage

This recipe has no required configuration parameters and comes from a rewrite core library. It can be activated directly without adding any dependencies.
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.search.FindDeprecatedUses")
}

repositories {
    mavenCentral()
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
            <recipe>org.openrewrite.java.search.FindDeprecatedUses</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.
{% code title="shell" %}
```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.activeRecipes=org.openrewrite.java.search.FindDeprecatedUses
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Find uses of deprecated methods](../../java/search/finddeprecatedmethods.md)
* [Find uses of deprecated classes](../../java/search/finddeprecatedclasses.md)
  * typePattern: ``
* [Find uses of deprecated fields](../../java/search/finddeprecatedfields.md)
  * typePattern: ``

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.search.FindDeprecatedUses
displayName: Find uses of deprecated classes, methods, and fields
description: Find deprecated uses of methods, fields, and types. Optionally ignore those classes that are inside deprecated scopes.
typePattern: 



recipeList:
  - org.openrewrite.java.search.FindDeprecatedMethods:
  - org.openrewrite.java.search.FindDeprecatedClasses:
      typePattern: 
  - org.openrewrite.java.search.FindDeprecatedFields:
      typePattern: 

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.search.FindDeprecatedUses)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
