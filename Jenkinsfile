node {


    env.GRADLE_HOME=${tool 'Gradle 8.4'}"
    env.M2_HOME="${tool 'Maven 3.9.5'}"

    stage("Clone Project") {
        git branch: 'main', url: 'https://github.com/respawnables/ci-cd-intro'
    }

    stage("Test") {
        sh "./gradlew clean test"
    }

    stage("Build Native Image") {
        def dockerHome = tool 'myDocker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
        sh "./gradlew clean bootBuildImage"
    }
}