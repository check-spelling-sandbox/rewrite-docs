# Migrate deprecated `javax.annotation.security` packages to `jakarta.annotation.security`

**org.openrewrite.java.migrate.jakarta.JavaxAnnotationSecurityPackageToJakarta**

_Change type of classes in the `javax.annotation.security` package to jakarta._

### Tags

* javax
* batch
* jakarta

## Source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/resources/META-INF/rewrite/jakarta-ee-9.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/1.21.1/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 1.21.1


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-migrate-java:1.21.1` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.migrate.jakarta.JavaxAnnotationSecurityPackageToJakarta")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-migrate-java:1.21.1")
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
            <recipe>org.openrewrite.java.migrate.jakarta.JavaxAnnotationSecurityPackageToJakarta</recipe>
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

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.migrate.jakarta.JavaxAnnotationSecurityPackageToJakarta
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `javax.annotation.security.DeclareRoles`
  * newFullyQualifiedTypeName: `jakarta.annotation.security.DeclareRoles`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `javax.annotation.security.DenyAll`
  * newFullyQualifiedTypeName: `jakarta.annotation.security.DenyAll`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `javax.annotation.security.PermitAll`
  * newFullyQualifiedTypeName: `jakarta.annotation.security.PermitAll`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `javax.annotation.security.RolesAllowed`
  * newFullyQualifiedTypeName: `jakarta.annotation.security.RolesAllowed`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `javax.annotation.security.RunAs`
  * newFullyQualifiedTypeName: `jakarta.annotation.security.RunAs`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.jakarta.JavaxAnnotationSecurityPackageToJakarta
displayName: Migrate deprecated `javax.annotation.security` packages to `jakarta.annotation.security`
description: Change type of classes in the `javax.annotation.security` package to jakarta.
tags:
  - javax
  - batch
  - jakarta
recipeList:
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: javax.annotation.security.DeclareRoles
      newFullyQualifiedTypeName: jakarta.annotation.security.DeclareRoles
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: javax.annotation.security.DenyAll
      newFullyQualifiedTypeName: jakarta.annotation.security.DenyAll
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: javax.annotation.security.PermitAll
      newFullyQualifiedTypeName: jakarta.annotation.security.PermitAll
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: javax.annotation.security.RolesAllowed
      newFullyQualifiedTypeName: jakarta.annotation.security.RolesAllowed
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: javax.annotation.security.RunAs
      newFullyQualifiedTypeName: jakarta.annotation.security.RunAs

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.migrate.jakarta.JavaxAnnotationSecurityPackageToJakarta)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
