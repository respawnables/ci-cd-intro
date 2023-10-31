node {

    env.JAVA_HOME="${tool 'JDK 21'}"
    env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"

    sh 'java -version'

    stage("Checkout") {
        scmCheckout()
    }

    stage("Build") {
        gradleBuild()
    }

    stage("Native Image Build") {
        dockerBuild()
    }

    stage("Docker Login"){
        dockerLogin()
    }

    stage("Docker Image Push"){
        dockerPush()
    }
}

def scmCheckout(){
    deleteDir()
    checkout scm
}

def gradleBuild(){
    sh "./gradlew clean test"
}

def dockerBuild(){
    sh "./gradlew clean bootBuildImage"
}

def dockerLogin(){
    withCredentials([usernamePassword(credentialsId: 'docker-push', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
        sh "docker login --username=${USERNAME} --password=${PASSWORD}"
    }

}

def dockerPush(){
    sh 'docker push respawnables/ci-cd-intro:latest'
}