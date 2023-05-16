# Migrate Spring Cloud Sleuth 3.1 to Micrometer Tracing 1.0

**org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing**

_Spring Cloud Sleuth has been discontinued and only compatible with Spring Boot 2.x._

### Tags

* spring
* cloud
* tracing
* sleuth
* micrometer

## Source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-cloud-2022.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/4.36.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 4.36.0

## Contributors
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)
* [Nick McKinney](mckinneynicholas@gmail.com)
* [Patrick](patway99@gmail.com)
* [Kyle Scully](scullykns@gmail.com)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-spring:4.36.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-spring:4.36.0")
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
            <recipe>org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>4.36.0</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-starter-sleuth`
  * newGroupId: `io.micrometer`
  * newArtifactId: `micrometer-tracing-bridge-brave`
  * newVersion: `1.0.x`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-otel-dependencies`
  * newGroupId: `io.micrometer`
  * newArtifactId: `micrometer-tracing-bridge-otel`
  * newVersion: `1.0.x`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-api`
  * newGroupId: `io.micrometer`
  * newArtifactId: `micrometer-tracing`
  * newVersion: `1.0.x`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-autoconfigure`
  * newGroupId: `org.springframework.boot`
  * newArtifactId: `spring-boot-actuator-autoconfigure`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-otel-autoconfigure`
  * newGroupId: `org.springframework.boot`
  * newArtifactId: `spring-boot-actuator-autoconfigure`
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `org.springframework.cloud`
  * oldArtifactId: `spring-cloud-sleuth-zipkin`
  * newGroupId: `io.zipkin.reporter2`
  * newArtifactId: `zipkin-reporter-brave`
  * newVersion: `2.16.x`
* [Add Maven dependency](../../../maven/adddependency.md)
  * groupId: `org.springframework.boot`
  * artifactId: `spring-boot-starter-actuator`
  * version: `3.0.x`
  * scope: `compile`
  * onlyIfUsing: `org.springframework.cloud.sleuth..*`
  * acceptTransitive: `true`
* [Add Maven dependency](../../../maven/adddependency.md)
  * groupId: `io.micrometer`
  * artifactId: `micrometer-tracing`
  * version: `1.0.x`
  * onlyIfUsing: `org.springframework.cloud.sleuth.annotation.*`
  * acceptTransitive: `true`
* [Add Maven dependency](../../../maven/adddependency.md)
  * groupId: `org.springframework.boot`
  * artifactId: `spring-boot-starter-aop`
  * version: `3.0.x`
  * onlyIfUsing: `org.springframework.cloud.sleuth.annotation.*`
  * acceptTransitive: `true`
* [Remove Maven dependency](../../../maven/removedependency.md)
  * groupId: `org.springframework.cloud`
  * artifactId: `spring-cloud-sleuth-*`
* [Remove Maven managed dependency](../../../maven/removemanageddependency.md)
  * groupId: `org.springframework.cloud`
  * artifactId: `spring-cloud-sleuth-*`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.cloud.sleuth.exporter.SpanFilter`
  * newFullyQualifiedTypeName: `io.micrometer.tracing.exporter.SpanExportingPredicate`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.cloud.sleuth.exporter.SpanIgnoringSpanFilter`
  * newFullyQualifiedTypeName: `io.micrometer.tracing.exporter.SpanIgnoringSpanExportingPredicate`
* [Rename package name](../../../java/changepackage.md)
  * oldPackageName: `org.springframework.cloud.sleuth.autoconfig`
  * newPackageName: `org.springframework.boot.actuate.autoconfigure.tracing`
  * recursive: `true`
* [Rename package name](../../../java/changepackage.md)
  * oldPackageName: `org.springframework.cloud.sleuth`
  * newPackageName: `io.micrometer.tracing`
  * recursive: `true`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.enabled`
  * newPropertyKey: `management.tracing.enabled`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.batch.enabled`
  * newPropertyKey: `management.tracing.enabled`
* [Delete a spring configuration property](../../../java/spring/deletespringproperty.md)
  * propertyKey: `spring.sleuth.supports-join`
* [Delete a spring configuration property](../../../java/spring/deletespringproperty.md)
  * propertyKey: `spring.sleuth.trace-id128`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.propagation.type`
  * newPropertyKey: `management.tracing.propagation.type`
* [Delete a spring configuration property](../../../java/spring/deletespringproperty.md)
  * propertyKey: `spring.sleuth.sampler.rate`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.sampler.probability`
  * newPropertyKey: `management.tracing.sampling.probability`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.baggage.remote-fields`
  * newPropertyKey: `management.tracing.baggage.remote-fields`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.propagation-keys`
  * newPropertyKey: `management.tracing.baggage.remote-fields`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.baggage.correlation-enabled`
  * newPropertyKey: `management.tracing.baggage.correlation.enabled`
* [Change the key of a spring application property](../../../java/spring/changespringpropertykey.md)
  * oldPropertyKey: `spring.sleuth.baggage.correlation-fields`
  * newPropertyKey: `management.tracing.baggage.correlation.fields`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing
displayName: Migrate Spring Cloud Sleuth 3.1 to Micrometer Tracing 1.0
description: Spring Cloud Sleuth has been discontinued and only compatible with Spring Boot 2.x.
tags:
  - spring
  - cloud
  - tracing
  - sleuth
  - micrometer
recipeList:
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-starter-sleuth
      newGroupId: io.micrometer
      newArtifactId: micrometer-tracing-bridge-brave
      newVersion: 1.0.x
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-otel-dependencies
      newGroupId: io.micrometer
      newArtifactId: micrometer-tracing-bridge-otel
      newVersion: 1.0.x
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-api
      newGroupId: io.micrometer
      newArtifactId: micrometer-tracing
      newVersion: 1.0.x
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-autoconfigure
      newGroupId: org.springframework.boot
      newArtifactId: spring-boot-actuator-autoconfigure
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-otel-autoconfigure
      newGroupId: org.springframework.boot
      newArtifactId: spring-boot-actuator-autoconfigure
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: org.springframework.cloud
      oldArtifactId: spring-cloud-sleuth-zipkin
      newGroupId: io.zipkin.reporter2
      newArtifactId: zipkin-reporter-brave
      newVersion: 2.16.x
  - org.openrewrite.maven.AddDependency:
      groupId: org.springframework.boot
      artifactId: spring-boot-starter-actuator
      version: 3.0.x
      scope: compile
      onlyIfUsing: org.springframework.cloud.sleuth..*
      acceptTransitive: true
  - org.openrewrite.maven.AddDependency:
      groupId: io.micrometer
      artifactId: micrometer-tracing
      version: 1.0.x
      onlyIfUsing: org.springframework.cloud.sleuth.annotation.*
      acceptTransitive: true
  - org.openrewrite.maven.AddDependency:
      groupId: org.springframework.boot
      artifactId: spring-boot-starter-aop
      version: 3.0.x
      onlyIfUsing: org.springframework.cloud.sleuth.annotation.*
      acceptTransitive: true
  - org.openrewrite.maven.RemoveDependency:
      groupId: org.springframework.cloud
      artifactId: spring-cloud-sleuth-*
  - org.openrewrite.maven.RemoveManagedDependency:
      groupId: org.springframework.cloud
      artifactId: spring-cloud-sleuth-*
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.cloud.sleuth.exporter.SpanFilter
      newFullyQualifiedTypeName: io.micrometer.tracing.exporter.SpanExportingPredicate
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.cloud.sleuth.exporter.SpanIgnoringSpanFilter
      newFullyQualifiedTypeName: io.micrometer.tracing.exporter.SpanIgnoringSpanExportingPredicate
  - org.openrewrite.java.ChangePackage:
      oldPackageName: org.springframework.cloud.sleuth.autoconfig
      newPackageName: org.springframework.boot.actuate.autoconfigure.tracing
      recursive: true
  - org.openrewrite.java.ChangePackage:
      oldPackageName: org.springframework.cloud.sleuth
      newPackageName: io.micrometer.tracing
      recursive: true
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.enabled
      newPropertyKey: management.tracing.enabled
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.batch.enabled
      newPropertyKey: management.tracing.enabled
  - org.openrewrite.java.spring.DeleteSpringProperty:
      propertyKey: spring.sleuth.supports-join
  - org.openrewrite.java.spring.DeleteSpringProperty:
      propertyKey: spring.sleuth.trace-id128
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.propagation.type
      newPropertyKey: management.tracing.propagation.type
  - org.openrewrite.java.spring.DeleteSpringProperty:
      propertyKey: spring.sleuth.sampler.rate
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.sampler.probability
      newPropertyKey: management.tracing.sampling.probability
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.baggage.remote-fields
      newPropertyKey: management.tracing.baggage.remote-fields
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.propagation-keys
      newPropertyKey: management.tracing.baggage.remote-fields
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.baggage.correlation-enabled
      newPropertyKey: management.tracing.baggage.correlation.enabled
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: spring.sleuth.baggage.correlation-fields
      newPropertyKey: management.tracing.baggage.correlation.fields

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.spring.cloud2022.MigrateCloudSleuthToMicrometerTracing)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
