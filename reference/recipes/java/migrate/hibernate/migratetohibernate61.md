# Migrate to Hibernate 6.1.x

**org.openrewrite.java.migrate.hibernate.MigrateToHibernate61**

_This recipe will apply changes commonly needed when migrating to Hibernate 6.1.x. The hibernate dependencies will   be updated to use the new org.hibernate.orm group ID and the recipe will make changes necessary to use Hibernate with Jakarta EE 9.0._

## Source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/resources/META-INF/rewrite/hibernate-6.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/1.21.1/jar)

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
    activeRecipe("org.openrewrite.java.migrate.hibernate.MigrateToHibernate61")
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
            <recipe>org.openrewrite.java.migrate.hibernate.MigrateToHibernate61</recipe>
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
  -Drewrite.activeRecipes=org.openrewrite.java.migrate.hibernate.MigrateToHibernate61
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Migrate Hibernate dependencies to 6.1.x](../../../java/migrate/hibernate/migratetohibernatedependencies61.md)
* [Migrate deprecated `javax.persistence` packages to `jakarta.persistence`](../../../java/migrate/jakarta/javaxpersistencetojakartapersistence.md)
* [Migrate xmlns entries in `persistence.xml` files](../../../java/migrate/jakarta/javaxpersistencexmltojakartapersistencexml.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.hibernate.MigrateToHibernate61
displayName: Migrate to Hibernate 6.1.x
description: This recipe will apply changes commonly needed when migrating to Hibernate 6.1.x. The hibernate dependencies will   be updated to use the new org.hibernate.orm group ID and the recipe will make changes necessary to use Hibernate with Jakarta EE 9.0.

recipeList:
  - org.openrewrite.java.migrate.hibernate.MigrateToHibernateDependencies61
  - org.openrewrite.java.migrate.jakarta.JavaxPersistenceToJakartaPersistence
  - org.openrewrite.java.migrate.jakarta.JavaxPersistenceXmlToJakartaPersistenceXml

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.migrate.hibernate.MigrateToHibernate61)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
