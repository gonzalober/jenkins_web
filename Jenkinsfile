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
          Document doc = Jsoup.parse(index.html);
          Elements p = doc.getElementsByTag("p");
          if(p == "Deployed by Jenkins job:") return true
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