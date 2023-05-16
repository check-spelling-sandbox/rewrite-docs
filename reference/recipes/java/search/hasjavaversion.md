# Find files compiled at a specific Java version

**org.openrewrite.java.search.HasJavaVersion**

_Finds Java source files matching a particular language level. This is useful especially as an applicable test for other recipes._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/java/org/openrewrite/java/search/HasJavaVersion.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-java/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 7.40.6

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Sam Snyder](sam@moderne.io)
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | version | An exact version number or node-style semver selector used to select the version number. |
| `Boolean` | checkTargetCompatibility | The source and target compatibility versions can be different. This option allows you to check against the target compatibility version instead of the source compatibility version. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.HasJavaVersionExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.HasJavaVersionExample
displayName: Find files compiled at a specific Java version example
recipeList:
  - org.openrewrite.java.search.HasJavaVersion:
      version: 17.X
      checkTargetCompatibility: 17.X
```
{% endcode %}

Now that `com.yourorg.HasJavaVersionExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.HasJavaVersionExample")
}

repositories {
    mavenCentral()
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
            <recipe>com.yourorg.HasJavaVersionExample</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.search.HasJavaVersion)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
