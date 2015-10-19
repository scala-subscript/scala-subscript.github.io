---
sectionid: getting-started
sectionclass: h2
title: Getting Started
parent-id: subscript
number: 1200
---
This section will describe how to create a simple "Hello World" application in SubScript from scratch.
To get started using SubScript:

1. Create a new SBT project, run the following commands:

  ```
  mkdir subscript-hello-world
  cd subscript-hello-world
  mkdir -pv src/main/scala
  touch build.sbt
  mkdir project
  touch project/build.sbt
  touch src/main/scala/Main.scala
  ```
  Here is a detailed description of what each of them do:
  1. Create a new directory which will be the root of the project. Hereafter, we'll assume it's name is `subscript-hello-world`: `mkdir subscript-hello-world`
  2. Cd to this directory: `cd subscript-hello-world`
  3. Create the directory for the sources: `mkdir -pv src/main/scala`
  4. Create the build file: `touch build.sbt`
  5. Create the project configuration directory: `mkdir project`
  6. Create the project configuration build file: `touch project/build.sbt`
  7. Create the main source file for your project: `touch src/main/scala/Main.scala`
2. In `project/build.sbt`, write the following code:
  
  {% highlight scala %}
  addSbtPlugin("org.subscript-lang" %% "subscript-sbt-plugin" % "1.0.0")
  {% endhighlight %}

  It adds the SubScript plugin to the SBT build tool, so that it can understand SubScript sources.
3. In `build.sbt`, write the following code:
  
{% highlight scala %}
scalaVersion := "2.11.7"
libraryDependencies += "org.subscript-lang" %% "subscript-swing" % "2.0.0"
SubscriptSbt.projectSettings
{% endhighlight %}

  First line sets the Scala version to be used, second sets a dependency on `subscript-swing` and third applies the SubScript SBT plugin.
  Note: you can declare a dependency on `"org.subscript-lang" %% "subscript-core" % "2.0.0"` instead of `subscript-swing`, but you need `subscript-swing` to be able to use the debugger.
4. In `src/main/scala/Main.scala`, write the following code:

{% highlight scala %}
import subscript.language

object Main {
  def main(args: Array[String]): Unit =
    subscript.DSL._execute(live)

  script live = {!println("Hello")!} {!println("World")!}
}
{% endhighlight %}

  Here, `import subscript.language` enables SubScript syntax in this file. Each file that needs to use SubScript syntax must have this top-level import.
  `subscript.DSL._execute(live)` calls a core SubScript method that executes the script provided as an argument.
  Finally, `script live = {!println("Hello")!} {!println("World")!}` is a simple script that prints "Hello World" from two Scala code blocks.
5. Execute the project by running `sbt run`
6. Debug the project with SubScript Graphical Debugger by running `sbt ssDebug`
7. To check out the official examples, go to the [examples repository](https://github.com/scala-subscript/examples) and follow its "Getting Started" guide

