node {
  stage("Clone project") {
    git branch: 'main', url: 'https://github.com/respawnables/ci-cd-intro'
  }

  stage("Build project with test execution") {
    sh "./gradlew build"
  }
}