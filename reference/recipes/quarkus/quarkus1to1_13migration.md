# Quarkus 1.13 migration from Quarkus 1.11

**org.openrewrite.quarkus.Quarkus1to1\_13Migration**

_Migrates Quarkus 1.11 to 1.13._

## Source

[GitHub](https://github.com/openrewrite/rewrite-quarkus/blob/main/src/main/resources/META-INF/rewrite/quarkus.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-quarkus/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-quarkus/1.19.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-quarkus
* version: 1.19.0


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-quarkus:1.19.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.quarkus.Quarkus1to1_13Migration")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-quarkus:1.19.0")
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
            <recipe>org.openrewrite.quarkus.Quarkus1to1_13Migration</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-quarkus</artifactId>
            <version>1.19.0</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-quarkus:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.quarkus.Quarkus1to1_13Migration
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Use `@ConfigMapping`](../quarkus/configpropertiestoconfigmapping.md)
* [Use Mutiny `multi.toHotStream()`](../quarkus/multitransformhotstreamtomultihotstream.md)
* [Use `native` profile in `quarkus-maven-plugin`](../quarkus/migratequarkusmavenpluginnativeimagegoal.md)
* [Configure `quarkus-maven-plugin` with reasonable defaults](../quarkus/configurequarkusmavenpluginwithreasonabledefaults.md)
* [Change property key](../properties/changepropertykey.md)
  * oldPropertyKey: `quarkus.dev.instrumentation`
  * newPropertyKey: `quarkus.live-reload.instrumentation`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.Multi collectItems()`
  * newMethodName: `collect`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.Multi groupItems()`
  * newMethodName: `group`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.Multi transform()`
  * newMethodName: `select`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.groups.MultiTransform byTakingFirstItems(..)`
  * newMethodName: `first`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.groups.MultiTransform byFilteringItemsWith(..)`
  * newMethodName: `where`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.Multi subscribeOn(java.util.concurrent.Executor)`
  * newMethodName: `runSubscriptionOn`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.Uni subscribeOn(java.util.concurrent.Executor)`
  * newMethodName: `runSubscriptionOn`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.groups.UniOnFailure apply(java.util.function.Function)`
  * newMethodName: `transform`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.groups.UniOnItem apply(java.util.function.Function)`
  * newMethodName: `transform`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.groups.UniOnItemOrFailure apply(java.util.function.BiFunction)`
  * newMethodName: `transform`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.groups.UniOnNotNull apply(java.util.function.Function)`
  * newMethodName: `transform`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.groups.MultiOnFailure apply(java.util.function.Function)`
  * newMethodName: `transform`
* [Change method name](../java/changemethodname.md)
  * methodPattern: `io.smallrye.mutiny.groups.MultiOnItem apply(java.util.function.Function)`
  * newMethodName: `transform`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.quarkus.Quarkus1to1_13Migration
displayName: Quarkus 1.13 migration from Quarkus 1.11
description: Migrates Quarkus 1.11 to 1.13.
recipeList:
  - org.openrewrite.quarkus.ConfigPropertiesToConfigMapping
  - org.openrewrite.quarkus.MultiTransformHotStreamToMultiHotStream
  - org.openrewrite.quarkus.MigrateQuarkusMavenPluginNativeImageGoal
  - org.openrewrite.quarkus.ConfigureQuarkusMavenPluginWithReasonableDefaults
  - org.openrewrite.properties.ChangePropertyKey:
      oldPropertyKey: quarkus.dev.instrumentation
      newPropertyKey: quarkus.live-reload.instrumentation
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.Multi collectItems()
      newMethodName: collect
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.Multi groupItems()
      newMethodName: group
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.Multi transform()
      newMethodName: select
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.groups.MultiTransform byTakingFirstItems(..)
      newMethodName: first
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.groups.MultiTransform byFilteringItemsWith(..)
      newMethodName: where
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.Multi subscribeOn(java.util.concurrent.Executor)
      newMethodName: runSubscriptionOn
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.Uni subscribeOn(java.util.concurrent.Executor)
      newMethodName: runSubscriptionOn
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.groups.UniOnFailure apply(java.util.function.Function)
      newMethodName: transform
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.groups.UniOnItem apply(java.util.function.Function)
      newMethodName: transform
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.groups.UniOnItemOrFailure apply(java.util.function.BiFunction)
      newMethodName: transform
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.groups.UniOnNotNull apply(java.util.function.Function)
      newMethodName: transform
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.groups.MultiOnFailure apply(java.util.function.Function)
      newMethodName: transform
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: io.smallrye.mutiny.groups.MultiOnItem apply(java.util.function.Function)
      newMethodName: transform

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.quarkus.Quarkus1to1_13Migration)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
