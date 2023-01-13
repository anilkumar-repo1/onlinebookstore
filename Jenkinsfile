pipeline {  
    agent any
    environment {
    registry = "docker1anil/bookstoreweb"
    registryCredential = dockerhub
    }
        stages {  
       	    stage("build artifact") {
           	    steps {  
              	    echo "building artifact"
              	    sh "mvn clean install"
              	    }
              	post {
                     success {
                             echo 'Now Archiving...'
                             archiveArtifacts artifacts: '**/target/*.war'
                                }
                            }
                 }
            stage('UNIT TEST'){
                     steps {
                                sh 'mvn test'
                            }
                        }
            stage('Build app image'){
                steps{
                script{
                dockerImage = docker.build registry + ":V$BUILD_NUMBER"
                }
                }

            }
            stage('Upload to dockerhub'){
            steps{
            scripts{
            docker.withRegistry('', registryCredential) {
                            dockerImage.push("V$BUILD_NUMBER")
                            dockerImage.push('latest')
            }
            }
            }
            }
        }
}
