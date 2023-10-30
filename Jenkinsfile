node {

  stage("Clone Project") {
    git branch: 'main', url: 'https://github.com/respawnables/ci-cd-intro'
  }

  stage("Test") {
    sh "./gradlew clean test"
  }

  stage('Initialize Docker'){
    def dockerHome = tool 'myDocker'
    env.PATH = "${dockerHome}/bin:${env.PATH}"
  }

  stage("Build Native Image") {
    sh "./gradlew clean bootBuildImage"
  }
}