node {

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