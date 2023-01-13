pipeline {  
    agent any  
        stages {  
       	    stage("build artifact") {
           	    steps {  
              	    echo "building artifact"
              	    sh "mvn clean install"
              	    }  
         	    } 
        }
}
