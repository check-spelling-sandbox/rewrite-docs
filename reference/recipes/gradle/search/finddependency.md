# Find Gradle dependency

**org.openrewrite.gradle.search.FindDependency**

_Finds dependencies declared in `build.gradle` files. See the [reference](https://docs.gradle.org/current/userguide/java_library_plugin.html#sec:java_library_configurations_graph) on Gradle configurations or the diagram below for a description of what configuration to use. A project's compile and runtime classpath is based on these configurations.

<img alt="Gradle compile classpath" src="https://docs.gradle.org/current/userguide/img/java-library-ignore-deprecated-main.png" width="200px"/>
 A project's test classpath is based on these configurations.

<img alt="Gradle test classpath" src="https://docs.gradle.org/current/userguide/img/java-library-ignore-deprecated-test.png" width="200px"/>._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-gradle/src/main/java/org/openrewrite/gradle/search/FindDependency.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-gradle/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 7.40.6

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Sam Snyder](sam@moderne.io)
* [Patrick](patway99@gmail.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | groupId | The first part of a dependency coordinate 'com.google.guava:guava:VERSION'. |
| `String` | artifactId | The second part of a dependency coordinate 'com.google.guava:guava:VERSION'. |
| `String` | configuration | *Optional*. The dependency configuration to search for dependencies in. If omitted then all configurations will be searched. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.FindDependencyExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.FindDependencyExample
displayName: Find Gradle dependency example
recipeList:
  - org.openrewrite.gradle.search.FindDependency:
      groupId: com.google.guava
      artifactId: guava
      configuration: api
```
{% endcode %}

Now that `com.yourorg.FindDependencyExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.FindDependencyExample")
}

repositories {
    mavenCentral()
}
```
{% endcode %}
{% endtab %}

{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.gradle.search.FindDependency)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
