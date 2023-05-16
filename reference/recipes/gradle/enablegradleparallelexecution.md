# Enable Gradle parallel execution

**org.openrewrite.gradle.EnableGradleParallelExecution**

_Most builds consist of more than one project and some of those projects are usually independent of one another. Yet Gradle will only run one task at a time by default, regardless of the project structure. By using the `--parallel` switch, you can force Gradle to execute tasks in parallel as long as those tasks are in different projects. See the [Gradle performance documentation](https://docs.gradle.org/current/userguide/performance.html#parallel_execution) for more information._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-gradle/src/main/resources/META-INF/rewrite/gradle.yml), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-gradle/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 7.40.6

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Nick McKinney](mckinneynicholas@gmail.com)
* [Tracey Yoshima](tracey.yoshima@gmail.com)


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
    activeRecipe("org.openrewrite.gradle.EnableGradleParallelExecution")
}

repositories {
    mavenCentral()
}

```
{% endcode %}
{% endtab %}

{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Add Gradle property](../gradle/addproperty.md)
  * key: `org.gradle.parallel`
  * value: `true`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.gradle.EnableGradleParallelExecution
displayName: Enable Gradle parallel execution
description: Most builds consist of more than one project and some of those projects are usually independent of one another. Yet Gradle will only run one task at a time by default, regardless of the project structure. By using the `--parallel` switch, you can force Gradle to execute tasks in parallel as long as those tasks are in different projects. See the [Gradle performance documentation](https://docs.gradle.org/current/userguide/performance.html#parallel_execution) for more information.
recipeList:
  - org.openrewrite.gradle.AddProperty:
      key: org.gradle.parallel
      value: true

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.gradle.EnableGradleParallelExecution)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
