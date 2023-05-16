# Create text file

**org.openrewrite.text.CreateTextFile**

_Creates a new plain text file._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-core/src/main/java/org/openrewrite/text/CreateTextFile.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-core/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-core
* version: 7.40.6

## Contributors
* [Scott Jungling](scott.jungling@gmail.com)
* [Jonathan Schnéider](jkschneider@gmail.com)
* [Tyler Van Gorder](1878529+tkvangorder@users.noreply.github.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | fileContents | Multiline text content for the file. |
| `String` | relativeFileName | File path of new file. |
| `Boolean` | overwriteExisting | *Optional*. If there is an existing file, should it be overwritten. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.CreateTextFileExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.CreateTextFileExample
displayName: Create text file example
recipeList:
  - org.openrewrite.text.CreateTextFile:
      fileContents: Some text.
      relativeFileName: foo/bar/baz.txt
      overwriteExisting: null
```
{% endcode %}

Now that `com.yourorg.CreateTextFileExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.CreateTextFileExample")
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
            <recipe>com.yourorg.CreateTextFileExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.text.CreateTextFile)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
