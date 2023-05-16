# Gradle dependency insight

**org.openrewrite.gradle.search.DependencyInsight**

_Find direct and transitive dependencies matching a group, artifact, and optionally a configuration name. Results include dependencies that either directly match or transitively include a matching dependency._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-gradle/src/main/java/org/openrewrite/gradle/search/DependencyInsight.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-gradle/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 7.40.6

## Contributors
* [Sam Snyder](sam@moderne.io)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Tim te Beek](tim@moderne.io)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | groupIdPattern | Group glob pattern used to match dependencies. |
| `String` | artifactIdPattern | Artifact glob pattern used to match dependencies. |
| `String` | configuration | *Optional*. Match dependencies with the specified scope. If not specified, all configurations will be searched. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.DependencyInsightExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.DependencyInsightExample
displayName: Gradle dependency insight example
recipeList:
  - org.openrewrite.gradle.search.DependencyInsight:
      groupIdPattern: com.fasterxml.jackson.module
      artifactIdPattern: jackson-module-*
      configuration: compileClasspath
```
{% endcode %}

Now that `com.yourorg.DependencyInsightExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.DependencyInsightExample")
}

repositories {
    mavenCentral()
}
```
{% endcode %}
{% endtab %}

{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.gradle.search.DependencyInsight)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
