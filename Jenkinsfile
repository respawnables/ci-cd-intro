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
    sh "docker login --username=respawnables --password=dckr_pat_d2SHQlpQd1kNO4Iln6VneelvMaA"
}

def dockerPush(){
    sh 'docker push respawnables/ci-cd-intro:latest'
}