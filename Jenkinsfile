@Library('jenkins_shared') _

pipeline {
  agent any

  options {
    timestamps()
  }
  stages {

    stage("Build") {
      steps {
        echo "Building"
        helloVariable("Gonzalo")
        script {
          utils.replaceString()
        }
      }
    }


    stage("Test") {
    parallel {
      stage('test replaceString Fx') {
        steps {
          sh """
            cat index.html | grep "Deployed by Jenkins job: ${BUILD_NUMBER}"
          """
        }
      }

      stage('test on window') {
        steps {
          echo "test"
        }
      }
     }
    }

    stage('deploy') {
      steps {
        echo "deploying"
      }
    }

    stage('print env variables') {
        steps {
            echo "print env variables"
        }
    }
  }

}