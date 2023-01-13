pipeline {  
    agent any  
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
        }
}
