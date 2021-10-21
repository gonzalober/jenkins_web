
@Library("jenkins_shared") _

pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Build"
                helloVariable("Fin")
                script {
                    utils.replaceString()
                }
            }
        }
        
        stage("Test"){
          parallel{
            stage("tests index grep") {
              steps{
                sh """
                cat index.html | grep "Deployed by Jenkins job: ${BUILD_NUMBER}"
                """
                }
              }
            stage("test on bash") {
              steps{
              sh "bash script.sh"
              }
            }
          }
        }
        
        stage("Deploy"){
            steps{
                echo "Deploy"
            }
        }
    }
}