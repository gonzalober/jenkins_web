
@Library("Jenkins_shared") _


pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Build"
                helloVariable("Fin")
                script{
                    utils.replaceString()
                }
            }
        }
        
      stage("Test"){
           steps {
               sh """
               cat index.html | grep "Deployed by Jenkins job: ${BUILD_NUMBER}"
               """
            }
        }
        
      stage("testing branches"){
          parallel{
            stage("Test on linux"){
                steps{
                    echo "Linux"
                }
            }
            stage("Test on windows"){
                steps{
                    echo "Windows"
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