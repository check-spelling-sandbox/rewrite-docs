# Properly use declaration-site type variance for well-known types

**org.openrewrite.java.cleanup.CommonDeclarationSiteTypeVariances**

_When using a method parameter like `Function<IN, OUT>`, it should rather be `Function<? super IN, ? extends OUT>`. This recipe checks for method parameters of well-known types._

### Tags

* RSPEC-1217

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/resources/META-INF/rewrite/cleanup.yml), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-java/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 7.40.6

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Sam Snyder](sam@moderne.io)


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
    activeRecipe("org.openrewrite.java.cleanup.CommonDeclarationSiteTypeVariances")
}

repositories {
    mavenCentral()
}

```
{% endcode %}
{% endtab %}
{% tab title="Maven POM" %}
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
            <recipe>org.openrewrite.java.cleanup.CommonDeclarationSiteTypeVariances</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.
{% code title="shell" %}
```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.activeRecipes=org.openrewrite.java.cleanup.CommonDeclarationSiteTypeVariances
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Properly use declaration-site type variance](../../java/cleanup/declarationsitetypevariance.md)
  * variantTypes: `[java.util.function.Consumer<IN>, java.util.function.BiPredicate<IN, IN>, java.util.function.DoubleFunction<OUT>, java.util.function.Function<IN, OUT>, java.util.function.IntFunction<OUT>, java.util.function.LongFunction<OUT>, java.util.function.ObjDoubleConsumer<IN>, java.util.function.ObjIntConsumer<IN>, java.util.function.ObjLongConsumer<IN>, java.util.function.Predicate<IN>, java.util.function.Supplier<OUT>, java.util.function.ToDoubleBiFunction<IN, IN>, java.util.function.ToDoubleFunction<IN>, java.util.function.ToIntBiFunction<IN, IN>, java.util.function.ToIntFunction<IN>, java.util.function.ToLongBiFunction<IN, IN>, java.util.function.ToLongFunction<IN>]`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.cleanup.CommonDeclarationSiteTypeVariances
displayName: Properly use declaration-site type variance for well-known types
description: When using a method parameter like `Function<IN, OUT>`, it should rather be `Function<? super IN, ? extends OUT>`. This recipe checks for method parameters of well-known types.
tags:
  - RSPEC-1217
recipeList:
  - org.openrewrite.java.cleanup.DeclarationSiteTypeVariance:
      variantTypes: [java.util.function.Consumer<IN>, java.util.function.BiPredicate<IN, IN>, java.util.function.DoubleFunction<OUT>, java.util.function.Function<IN, OUT>, java.util.function.IntFunction<OUT>, java.util.function.LongFunction<OUT>, java.util.function.ObjDoubleConsumer<IN>, java.util.function.ObjIntConsumer<IN>, java.util.function.ObjLongConsumer<IN>, java.util.function.Predicate<IN>, java.util.function.Supplier<OUT>, java.util.function.ToDoubleBiFunction<IN, IN>, java.util.function.ToDoubleFunction<IN>, java.util.function.ToIntBiFunction<IN, IN>, java.util.function.ToIntFunction<IN>, java.util.function.ToLongBiFunction<IN, IN>, java.util.function.ToLongFunction<IN>]

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.cleanup.CommonDeclarationSiteTypeVariances)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
