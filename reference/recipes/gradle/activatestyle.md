# Activate Style in Gradle Project

**org.openrewrite.gradle.ActivateStyle**

_Sets the specified style as active. Once the style has been set, future recipes will use the specified style for any changes they make. This recipe does not reformat anything on its own. Prefers to set the `activeStyle()` method in the `rewrite` DSL in a build.gradle.If no `rewrite` DSL can be found to update, will instead place a "systemProp.rewrite.activeStyles" entry within the project's gradle.properties. Styles can be provided by rewrite itself, defined in a rewrite.yml, or provided by recipe modules._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-gradle/src/main/java/org/openrewrite/gradle/ActivateStyle.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-gradle/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 7.40.6

## Contributors
* [Sam Snyder](sam@moderne.io)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Tracey Yoshima](tracey.yoshima@gmail.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | fullyQualifiedStyleName | The name of the style to activate. |
| `boolean` | overwriteExistingStyles | *Optional*. When set to `true` this Recipe will clear all existing active styles. When `false` the new style will be added after existing styles. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ActivateStyleExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ActivateStyleExample
displayName: Activate Style in Gradle Project example
recipeList:
  - org.openrewrite.gradle.ActivateStyle:
      fullyQualifiedStyleName: org.openrewrite.java.IntelliJ
      overwriteExistingStyles: null
```
{% endcode %}

Now that `com.yourorg.ActivateStyleExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.ActivateStyleExample")
}

repositories {
    mavenCentral()
}
```
{% endcode %}
{% endtab %}

{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.gradle.ActivateStyle)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
