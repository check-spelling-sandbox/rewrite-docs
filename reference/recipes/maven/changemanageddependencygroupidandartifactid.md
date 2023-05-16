# Change Maven managed dependency groupId, artifactId and optionally the version

**org.openrewrite.maven.ChangeManagedDependencyGroupIdAndArtifactId**

_Change the groupId, artifactId and optionally the version of a specified Maven managed dependency._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-maven/src/main/java/org/openrewrite/maven/ChangeManagedDependencyGroupIdAndArtifactId.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-maven/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-maven
* version: 7.40.6

## Example
* Example 1: 

## Contributors
* [Jonathan Leitschuh](jonathan.leitschuh@gmail.com)
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Sam Snyder](sam@moderne.io)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | oldGroupId | The old groupId to replace. The groupId is the first part of a managed dependency coordinate 'com.google.guava:guava:VERSION'. |
| `String` | oldArtifactId | The old artifactId to replace. The artifactId is the second part of a managed dependency coordinate 'com.google.guava:guava:VERSION'. |
| `String` | newGroupId | The new groupId to use. |
| `String` | newArtifactId | The new artifactId to use. |
| `String` | newVersion | *Optional*. The new version to use. |
| `String` | versionPattern | *Optional*. Allows version selection to be extended beyond the original Node Semver semantics. So for example,Setting 'version' to "25-29" can be paired with a metadata pattern of "-jre" to select Guava 29.0-jre |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ChangeManagedDependencyGroupIdAndArtifactIdExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ChangeManagedDependencyGroupIdAndArtifactIdExample
displayName: Change Maven managed dependency groupId, artifactId and optionally the version example
recipeList:
  - org.openrewrite.maven.ChangeManagedDependencyGroupIdAndArtifactId:
      oldGroupId: org.openrewrite.recipe
      oldArtifactId: rewrite-testing-frameworks
      newGroupId: corp.internal.openrewrite.recipe
      newArtifactId: rewrite-testing-frameworks
      newVersion: 2.0.0
      versionPattern: '-jre'
```
{% endcode %}

Now that `com.yourorg.ChangeManagedDependencyGroupIdAndArtifactIdExample` has been defined activate it in your build file:
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
            <recipe>com.yourorg.ChangeManagedDependencyGroupIdAndArtifactIdExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.maven.ChangeManagedDependencyGroupIdAndArtifactId)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
