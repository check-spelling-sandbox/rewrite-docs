# Common static analysis issues

**org.openrewrite.java.cleanup.CommonStaticAnalysis**

_Resolve common static analysis issues discovered through 3rd party tools._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/resources/META-INF/rewrite/static-analysis-cleanup.yml), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-java/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 7.40.6

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Patrick Way](pway99@users.noreply.github.com)
* [Patrick](patway99@gmail.com)
* [Sam Snyder](sam@moderne.io)
* [Tracey Yoshima](tracey.yoshima@gmail.com)
* [Aaron Gershman](aegershman@gmail.com)
* [Jonathan Leitschuh](jonathan.leitschuh@gmail.com)
* [Kun Li](kun@moderne.io)
* [Knut Wannheden](knut.wannheden@mobi.ch)
* [Guliver](Guliver@users.noreply.github.com)
* [traceyyoshima](tracey.yoshima@gmail.com)
* [Knut Wannheden](knut@moderne.io)
* [Kun Li](122563761+kunli2@users.noreply.github.com)
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)
* [Tyler Van Gorder](1878529+tkvangorder@users.noreply.github.com)
* [Nick McKinney](mckinneynicholas@gmail.com)
* [Greg Adams](greg@moderne.io)
* [Knut Wannheden](knut.wannheden@gmail.com)
* [Grzegorz Olędzki](grzegon@poczta.onet.pl)
* [Jonathan Schnéider](jkschneider@gmail.com)
* [Scott Jungling](scott.jungling@gmail.com)
* [mrbitrary](84456251+mrbitrary@users.noreply.github.com)
* [Martin Panzer](postremus1996@googlemail.com)
* [Mike Solomon](mike@moderne.io)


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
    activeRecipe("org.openrewrite.java.cleanup.CommonStaticAnalysis")
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
            <recipe>org.openrewrite.java.cleanup.CommonStaticAnalysis</recipe>
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
  -Drewrite.activeRecipes=org.openrewrite.java.cleanup.CommonStaticAnalysis
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Add `serialVersionUID` to a `Serializable` class when missing](../../java/cleanup/addserialversionuidtoserializable.md)
* [Atomic Boolean, Integer, and Long equality checks compare their values](../../java/cleanup/atomicprimitiveequalsusesget.md)
* [`BigDecimal` rounding constants to `RoundingMode` enums](../../java/cleanup/bigdecimalroundingconstantstoenums.md)
* [Boolean checks should not be inverted](../../java/cleanup/booleanchecksnotinverted.md)
* [CaseInsensitive comparisons do not alter case](../../java/cleanup/caseinsensitivecomparisonsdonotchangecase.md)
* [Catch clause should do more than just rethrow](../../java/cleanup/catchclauseonlyrethrows.md)
* [Chain `StringBuilder.append()` calls](../../java/cleanup/chainstringbuilderappendcalls.md)
* [Covariant equals](../../java/cleanup/covariantequals.md)
* [Default comes last](../../java/cleanup/defaultcomeslast.md)
* [Remove empty blocks](../../java/cleanup/emptyblock.md)
* [Equals avoids null](../../java/cleanup/equalsavoidsnull.md)
* [Explicit initialization](../../java/cleanup/explicitinitialization.md)
* [`Externalizable` classes have no-arguments constructor](../../java/cleanup/externalizablehasnoargsconstructor.md)
* [Finalize private fields](../../java/cleanup/finalizeprivatefields.md)
* [Fall through](../../java/cleanup/fallthrough.md)
* [Finalize classes with private constructors](../../java/cleanup/finalclass.md)
* [Fix `String#format` and `String#formatted` expressions](../../java/cleanup/fixstringformatexpressions.md)
* [`for` loop counters incremented in update](../../java/cleanup/forloopincrementinupdate.md)
* [Use `indexOf(String, int)`](../../java/cleanup/indexofchecksshoulduseastartposition.md)
* [`indexOf()` replaceable by `contains()`](../../java/cleanup/indexofreplaceablebycontains.md)
* [`indexOf` should not compare greater than zero](../../java/cleanup/indexofshouldnotcomparegreaterthanzero.md)
* [Inline variable](../../java/cleanup/inlinevariable.md)
* [Use `Collection#isEmpty()` instead of comparing `size()`](../../java/cleanup/isemptycalloncollections.md)
* [Simplify lambda blocks to expressions](../../java/cleanup/lambdablocktoexpression.md)
* [Rename packages to lowercase](../../java/cleanup/lowercasepackage.md)
* [Method name casing](../../java/cleanup/methodnamecasing.md)
* [`switch` statements should have at least 3 `case` clauses](../../java/cleanup/minimumswitchcases.md)
* [Modifier order](../../java/cleanup/modifierorder.md)
* [No multiple variable declarations](../../java/cleanup/multiplevariabledeclarations.md)
* [Fix missing braces](../../java/cleanup/needbraces.md)
* [Nested enums are not static](../../java/cleanup/nestedenumsarenotstatic.md)
* [Change `StringBuilder` and `StringBuffer` character constructor argument to `String`](../../java/cleanup/newstringbuilderbufferwithcharargument.md)
* [No double brace initialization](../../java/cleanup/nodoublebraceinitialization.md)
* [Use `Collections#emptyList()`, `emptyMap()`, and `emptySet()`](../../java/cleanup/noemptycollectionwithrawtype.md)
* [Use comparison rather than equality checks in for conditions](../../java/cleanup/noequalityinforcondition.md)
* [Remove `finalize()` method](../../java/cleanup/nofinalizer.md)
* [No primitive wrappers for #toString() or #compareTo(..)](../../java/cleanup/noprimitivewrappersfortostringorcompareto.md)
* [Jump statements should not be redundant](../../java/cleanup/noredundantjumpstatements.md)
* [Unnecessary String#toString()](../../java/cleanup/notostringonstringtype.md)
* [Unnecessary String#valueOf(..)](../../java/cleanup/novalueofonstringtype.md)
* [`finalize()` calls super](../../java/cleanup/objectfinalizecallssuper.md)
* [Use primitive wrapper `valueOf` method](../../java/cleanup/primitivewrapperclassconstructortovalueof.md)
* [Redundant file creation](../../java/cleanup/redundantfilecreation.md)
* [Remove extra semicolons](../../java/cleanup/removeextrasemicolons.md)
* [Reformat local variable names to camelCase](../../java/cleanup/renamelocalvariablestocamelcase.md)
* [Rename methods named `hashcode`, `equal`, or `tostring`](../../java/cleanup/renamemethodsnamedhashcodeequalortostring.md)
* [Reformat private field names to camelCase](../../java/cleanup/renameprivatefieldstocamelcase.md)
* [Use method references in lambda](../../java/cleanup/replacelambdawithmethodreference.md)
* [Replace StringBuilder.append() with String](../../java/cleanup/replacestringbuilderwithstring.md)
* [Simplify boolean expression](../../java/cleanup/simplifybooleanexpression.md)
* [Simplify boolean return](../../java/cleanup/simplifybooleanreturn.md)
* [Static methods not final](../../java/cleanup/staticmethodnotfinal.md)
* [Use `String.equals()` on String literals](../../java/cleanup/stringliteralequality.md)
* [Unnecessary close in try-with-resources](../../java/cleanup/unnecessarycloseintrywithresources.md)
* [Unnecessary explicit type arguments](../../java/cleanup/unnecessaryexplicittypearguments.md)
* [Remove unnecessary parentheses](../../java/cleanup/unnecessaryparentheses.md)
* [Remove Nullable and CheckForNull annotations from primitives](../../java/cleanup/unnecessaryprimitiveannotations.md)
* [Upper case literal suffixes](../../java/cleanup/uppercaseliteralsuffixes.md)
* [Use diamond operator](../../java/cleanup/usediamondoperator.md)
* [No C-style array declarations](../../java/cleanup/usejavastylearraydeclarations.md)
* [Use lambdas expression to replace anonymous class where possible](../../java/cleanup/uselambdaforfunctionalinterface.md)
* [Prefer `while` over `for` loops](../../java/cleanup/whileinsteadoffor.md)
* [Write octal values as decimal](../../java/cleanup/writeoctalvaluesasdecimal.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.cleanup.CommonStaticAnalysis
displayName: Common static analysis issues
description: Resolve common static analysis issues discovered through 3rd party tools.
recipeList:
  - org.openrewrite.java.cleanup.AddSerialVersionUidToSerializable
  - org.openrewrite.java.cleanup.AtomicPrimitiveEqualsUsesGet
  - org.openrewrite.java.cleanup.BigDecimalRoundingConstantsToEnums
  - org.openrewrite.java.cleanup.BooleanChecksNotInverted
  - org.openrewrite.java.cleanup.CaseInsensitiveComparisonsDoNotChangeCase
  - org.openrewrite.java.cleanup.CatchClauseOnlyRethrows
  - org.openrewrite.java.cleanup.ChainStringBuilderAppendCalls
  - org.openrewrite.java.cleanup.CovariantEquals
  - org.openrewrite.java.cleanup.DefaultComesLast
  - org.openrewrite.java.cleanup.EmptyBlock
  - org.openrewrite.java.cleanup.EqualsAvoidsNull
  - org.openrewrite.java.cleanup.ExplicitInitialization
  - org.openrewrite.java.cleanup.ExternalizableHasNoArgsConstructor
  - org.openrewrite.java.cleanup.FinalizePrivateFields
  - org.openrewrite.java.cleanup.FallThrough
  - org.openrewrite.java.cleanup.FinalClass
  - org.openrewrite.java.cleanup.FixStringFormatExpressions
  - org.openrewrite.java.cleanup.ForLoopIncrementInUpdate
  - org.openrewrite.java.cleanup.IndexOfChecksShouldUseAStartPosition
  - org.openrewrite.java.cleanup.IndexOfReplaceableByContains
  - org.openrewrite.java.cleanup.IndexOfShouldNotCompareGreaterThanZero
  - org.openrewrite.java.cleanup.InlineVariable
  - org.openrewrite.java.cleanup.IsEmptyCallOnCollections
  - org.openrewrite.java.cleanup.LambdaBlockToExpression
  - org.openrewrite.java.cleanup.LowercasePackage
  - org.openrewrite.java.cleanup.MethodNameCasing:
  - org.openrewrite.java.cleanup.MinimumSwitchCases
  - org.openrewrite.java.cleanup.ModifierOrder
  - org.openrewrite.java.cleanup.MultipleVariableDeclarations
  - org.openrewrite.java.cleanup.NeedBraces
  - org.openrewrite.java.cleanup.NestedEnumsAreNotStatic
  - org.openrewrite.java.cleanup.NewStringBuilderBufferWithCharArgument
  - org.openrewrite.java.cleanup.NoDoubleBraceInitialization
  - org.openrewrite.java.cleanup.NoEmptyCollectionWithRawType
  - org.openrewrite.java.cleanup.NoEqualityInForCondition
  - org.openrewrite.java.cleanup.NoFinalizer
  - org.openrewrite.java.cleanup.NoPrimitiveWrappersForToStringOrCompareTo
  - org.openrewrite.java.cleanup.NoRedundantJumpStatements
  - org.openrewrite.java.cleanup.NoToStringOnStringType
  - org.openrewrite.java.cleanup.NoValueOfOnStringType
  - org.openrewrite.java.cleanup.ObjectFinalizeCallsSuper
  - org.openrewrite.java.cleanup.PrimitiveWrapperClassConstructorToValueOf
  - org.openrewrite.java.cleanup.RedundantFileCreation
  - org.openrewrite.java.cleanup.RemoveExtraSemicolons
  - org.openrewrite.java.cleanup.RenameLocalVariablesToCamelCase
  - org.openrewrite.java.cleanup.RenameMethodsNamedHashcodeEqualOrTostring
  - org.openrewrite.java.cleanup.RenamePrivateFieldsToCamelCase
  - org.openrewrite.java.cleanup.ReplaceLambdaWithMethodReference
  - org.openrewrite.java.cleanup.ReplaceStringBuilderWithString
  - org.openrewrite.java.cleanup.SimplifyBooleanExpression
  - org.openrewrite.java.cleanup.SimplifyBooleanReturn
  - org.openrewrite.java.cleanup.StaticMethodNotFinal
  - org.openrewrite.java.cleanup.StringLiteralEquality
  - org.openrewrite.java.cleanup.UnnecessaryCloseInTryWithResources
  - org.openrewrite.java.cleanup.UnnecessaryExplicitTypeArguments
  - org.openrewrite.java.cleanup.UnnecessaryParentheses
  - org.openrewrite.java.cleanup.UnnecessaryPrimitiveAnnotations
  - org.openrewrite.java.cleanup.UpperCaseLiteralSuffixes
  - org.openrewrite.java.cleanup.UseDiamondOperator
  - org.openrewrite.java.cleanup.UseJavaStyleArrayDeclarations
  - org.openrewrite.java.cleanup.UseLambdaForFunctionalInterface
  - org.openrewrite.java.cleanup.WhileInsteadOfFor
  - org.openrewrite.java.cleanup.WriteOctalValuesAsDecimal

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.cleanup.CommonStaticAnalysis)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
