# Change method target to static

**org.openrewrite.java.ChangeMethodTargetToStatic**

_Change method invocations to static method calls._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/java/org/openrewrite/java/ChangeMethodTargetToStatic.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-java/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 7.40.6

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Nick McKinney](mckinneynicholas@gmail.com)
* [Greg Adams](greg@moderne.io)
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)
* [traceyyoshima](tracey.yoshima@gmail.com)
* [Sam Snyder](sam@moderne.io)
* [Aaron Gershman](aegershman@gmail.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | methodPattern | A [method pattern](/reference/method-patterns.md) that is used to find matching method invocations. The original method call may or may not be a static method invocation. |
| `String` | fullyQualifiedTargetTypeName | A fully-qualified class name of the type upon which the static method is defined. |
| `String` | returnType | *Optional*. Sometimes changing the target type also changes the return type. In the Guava example, changing from `ImmutableSet#of(..)` to `Set#of(..)` widens the return type from Guava's `ImmutableSet` to just `java.util.Set`. |
| `Boolean` | matchOverrides | *Optional*. When enabled, find methods that are overrides of the [method pattern](/reference/method-patterns.md). |
| `Boolean` | matchUnknownTypes | *Optional*. When enabled, include method invocations which appear to match if full type information is missing. Using matchUnknownTypes can improve recipe resiliency for an AST with missing type information, but also increases the risk of false-positive matches on unrelated method invocations. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ChangeMethodTargetToStaticExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ChangeMethodTargetToStaticExample
displayName: Change method target to static example
recipeList:
  - org.openrewrite.java.ChangeMethodTargetToStatic:
      methodPattern: com.google.common.collect.ImmutableSet of(..)
      fullyQualifiedTargetTypeName: java.util.Set
      returnType: java.util.Set
      matchOverrides: null
      matchUnknownTypes: null
```
{% endcode %}

Now that `com.yourorg.ChangeMethodTargetToStaticExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.ChangeMethodTargetToStaticExample")
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
            <recipe>com.yourorg.ChangeMethodTargetToStaticExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.ChangeMethodTargetToStatic)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
