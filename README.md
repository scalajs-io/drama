Drama API for Scala.js
================================
[drama](https://www.npmjs.com/package/drama) - A drama library for NodeJS.

### Description

Actor model implementation for JavaScript and Node.js (work in progress)

### Build Dependencies

* [SBT v0.13.13](http://www.scala-sbt.org/download.html)

### Build/publish the SDK locally

```bash
 $ sbt clean publish-local
```

### Running the tests

Before running the tests the first time, you must ensure the npm packages are installed:

```bash
$ npm install
```

Then you can run the tests:

```bash
$ sbt test
```

### Examples

```scala
import io.scalajs.npm.drama._
import scala.scalajs.js
import scala.scalajs.js.annotation.ScalaJSDefined

val actorSystem = Drama("sys")

val actor = actorSystem.actor(new GreetingActor())
actor ! "sayHello" -> "Hello"
actor ! "sayHello" -> "Bon jour"
actor ! "sayHello" -> "Buenos dias"

/**
  * Greeting Actor
  * @author lawrence.daniels@gmail.com
  */
@ScalaJSDefined
class GreetingActor() extends js.Object {

  def sayHello(message: String): Unit = println("Received: %s", message)

}
```

### Artifacts and Resolvers

To add the `Drama` binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "drama" % "0.4.0"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
```