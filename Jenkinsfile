def printFromFunction() {
  println("I am printing from a function")
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
        printFromFunction()
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