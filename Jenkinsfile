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
          utils.printFromFunction()
        }
      }
    }


    stage("Test") {
    parallel {
      stage('test on linux') {
        steps {
          echo "test"
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