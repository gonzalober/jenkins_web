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
   
      stage('test replaceString Fx') {
        steps {
          sh """
            cat index.html | grep "Deployed by Jenkins job: ${BUILD_NUMBER}"
          """
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