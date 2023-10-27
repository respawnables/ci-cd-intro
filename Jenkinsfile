node {
  stage("Clone project") {
    git branch: 'main', url: 'https://github.com/respawnables/ci-cd-intro'
  }

  stage("Test") {
    sh "./gradlew clean test"
  }

  stage("Build Native Image") {
    sh "./gradlew clean bootBuildImage"
  }
}