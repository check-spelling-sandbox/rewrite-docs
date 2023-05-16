# Use Maven Compiler Plugin Release Configuration

**org.openrewrite.java.migrate.maven.UseMavenCompilerPluginReleaseConfiguration**

_Replaces any explicit `source` or `target` configuration (if present) on the maven-compiler-plugin with `release`, and updates the `release` value if needed. Will not downgrade the java version if the current version is higher._

## Source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/java/org/openrewrite/java/migrate/maven/UseMavenCompilerPluginReleaseConfiguration.java), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/1.21.1/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 1.21.1

## Contributors
* [Nick McKinney](mckinneynicholas@gmail.com)
* [Sam Snyder](sam@moderne.io)
* [Jonathan Schnéider](jkschneider@gmail.com)
* [traceyyoshima](tracey.yoshima@gmail.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | releaseVersion | The new value for the release configuration. This recipe prefers ${java.version} if defined. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.UseMavenCompilerPluginReleaseConfigurationExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.UseMavenCompilerPluginReleaseConfigurationExample
displayName: Use Maven Compiler Plugin Release Configuration example
recipeList:
  - org.openrewrite.java.migrate.maven.UseMavenCompilerPluginReleaseConfiguration:
      releaseVersion: 11
```
{% endcode %}

Now that `com.yourorg.UseMavenCompilerPluginReleaseConfigurationExample` has been defined activate it and take a dependency on org.openrewrite.recipe:rewrite-migrate-java:1.21.1 in your build file:
{% tabs %}

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
            <recipe>com.yourorg.UseMavenCompilerPluginReleaseConfigurationExample</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-migrate-java</artifactId>
            <version>1.21.1</version>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.migrate.maven.UseMavenCompilerPluginReleaseConfiguration)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
