See `my-tasks.gradle`.

Demonstrates the following concepts:

1. Creating custom tasks with dependencies: `taskB` is dependent on `taskA`.
2. Using [upToDateWhen](https://docs.gradle.org/current/javadoc/org/gradle/api/tasks/TaskOutputs.html#upToDateWhen(groovy.lang.Closure))
   to to only run `taskB` if `taskA` also ran.
3. Using [onlyIf](https://docs.gradle.org/current/javadoc/org/gradle/api/Task.html#onlyIf(groovy.lang.Closure))
   to optionally disable `taskA` if the `skip` command-line property is specified.
4. How to use [afterEvaluate](https://docs.gradle.org/current/userguide/build_lifecycle.html) to make a
   task a dependency of another task.
   In this case, we make all `Test` tasks dependent on my custom task `taskB`.

Examples:

Execute both taskA and taskB before running the unit tests:

    ./gradlew testDebug

Skip both taskA and taskB:

    ./gradlew testDebug -Pskip

Also see how to use [setDidWork](https://docs.gradle.org/current/javadoc/org/gradle/api/Task.html#setDidWork(boolean))
in your task action for even more flexibility...
