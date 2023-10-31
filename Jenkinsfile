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