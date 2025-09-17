# hello-java-no-docker

Minimal Java project that builds with `javac` (no Maven/Gradle/Docker required).

## Jenkins setup
- Create **Pipeline (from SCM)** pointing to this repo.
- The provided `Jenkinsfile` will:
  1) checkout this repo,
  2) compile `src/Hello.java` into `build/`,
  3) run a tiny test that asserts the output equals "Hello, Jenkins!",
  4) archive build artifacts.

If you use **Pipeline script** (not from SCM), remove the `checkout scm` step or replace it with `sh 'ls -la'`.
