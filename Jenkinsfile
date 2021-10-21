pipeline {
  agent any

  options {
    timestamps()
  }
  stages {

    stage("Build") {
      steps {
        echo "Building"
      }
    }

    stage('test on linux') {
      steps {
        echo "test"
      }
    }

     stage('test on window') {
      steps {
        echo "test"
    }

    stage('deploy') {
      steps {
        echo "deploying"
    }

    stage('print env variables') {
        steps {
            echo "print env variables"
        }
  }

}