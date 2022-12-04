pipeline {
    agent any
     tools {
        maven 'Maven' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat_details', path: '', url: 'http://localhost:8085')], contextPath: '/app', war: '**/*.war'
              
            }
            
        }

    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
             
        }
        failure{
            echo "========pipeline execution failed========"  
        }
     }
  }
}     
