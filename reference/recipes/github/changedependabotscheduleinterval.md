# Change dependabot schedule interval

**org.openrewrite.github.ChangeDependabotScheduleInterval**

_Change the schedule interval for a given package-ecosystem in a `dependabot.yml` configuration file. [The available configuration options for dependabot are listed on GitHub](https://docs.github.com/en/code-security/supply-chain-security/keeping-your-dependencies-updated-automatically/configuration-options-for-dependency-updates)._

### Tags

* github
* dependabot
* dependencies

## Source

[GitHub](https://github.com/openrewrite/rewrite-github-actions/blob/main/src/main/java/org/openrewrite/github/ChangeDependabotScheduleInterval.java), [Issue Tracker](https://github.com/openrewrite/rewrite-github-actions/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-github-actions/1.20.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-github-actions
* version: 1.20.0

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | packageEcosystem | The package-ecosystem to make updates on. |
| `String` | interval | The schedule interval value the package-ecosystem should use. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ChangeDependabotScheduleIntervalExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ChangeDependabotScheduleIntervalExample
displayName: Change dependabot schedule interval example
recipeList:
  - org.openrewrite.github.ChangeDependabotScheduleInterval:
      packageEcosystem: maven
      interval: weekly
```
{% endcode %}

Now that `com.yourorg.ChangeDependabotScheduleIntervalExample` has been defined activate it and take a dependency on org.openrewrite.recipe:rewrite-github-actions:1.20.0 in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.ChangeDependabotScheduleIntervalExample")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-github-actions:1.20.0")
}
```
{% endcode %}
{% endtab %}
{% tab title="Maven" %}
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
            <recipe>com.yourorg.ChangeDependabotScheduleIntervalExample</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-github-actions</artifactId>
            <version>1.20.0</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.github.ChangeDependabotScheduleInterval)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
