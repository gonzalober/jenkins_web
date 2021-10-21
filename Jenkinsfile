@Library('jenkins_shared') _

def printFromFunction() {
  println("I am printing from a function")
}

def replaceString() {
  def text = readFile file: "index.html"
  text = text.replaceAll("%BUILD_NUMBER%", "${BUILD_NUMBER}")
  writeFile file: "index.html", text: text
}

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