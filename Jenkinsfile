
@Library("jenkins_shared") _

pipeline{
    agent any

    options {
      timestamps()
    }

    environment {
      MYENVVAR = "testenvar"
      GITHUB = credentials("github")
    }

    parameters {
      string(name: 'Name', defaultValue: 'Gonzalo', description: 'Your name')
    }

    stages{
        stage("Build"){
            steps{
                echo "Building"
                echo "${MYENVVAR}"
                echo "${params.Name}"
                helloVariable("Fin")
                script {
                    utils.replaceString()
                }
            }
        }

        stage("Docker Build"){
          agent {
            docker {
              image: "node: latest"
              args: "-v ${WORKSPACE}/docker:/home/node"
            }
          }
        }
            steps{
                sh """
                  node --version>/home/node/docker_node_version
                  npm --version>/home/node/docker_npm_version
                """
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
                  sshPublisher(publishers: [sshPublisherDesc(configName: 'http', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'mv index.html /var/www/html', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'index.html')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
    post {
      always {
        archiveArtifacts artifacts: 'index.html', followSymlinks: false
      }
    }
}
      // cleanup{
      //   cleanWs()
      // }
    
