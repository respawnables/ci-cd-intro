node {
  stage("Clone project") {
    git branch: 'main', url: 'https://github.com/respawnables/ci-cd-intro'
  }

  stage("Test") {
    sh "./gradlew clean test"
  }

  stage("Gradle Build") {
    sh "./gradlew build"
  }
}