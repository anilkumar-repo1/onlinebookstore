pipeline {  
    agent any
    environment {
    registry = docker1anil/bookstoreweb
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
                dockerimage = docker.build registry + 'V$BUILD_NUMBER'
                }
                }

            }
        }
}
