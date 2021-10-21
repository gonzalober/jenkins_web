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
          pDOM.small.findAll{
          String[] text = it.localText();
          }
          if(text[0].equals("Deployed by Jenkins job") == "Deployed by Jenkins job:") return true
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