pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/vijaykommana/demo-counter-app.git'
                }
            }
        }
        stage('UNIT testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        stage('Integration testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('Maven build'){
            
            steps{
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        stage('nexus'){
            steps{
                script{
                    nexusArtifactUploader artifacts: 
                    [
                        [artifactId: 'springboot', 
                        classifier: '', file: 'target/Uber.jar',
                         type: 'jar'
                         ]
                         ], 
                         credentialsId: 'nexus',
                          groupId: 'com.example',
                           nexusUrl: '52.11.16.44:8081',
                            nexusVersion: 'nexus3',
                             protocol: 'http', 
                             repository: 'vijay-release', 
                             version: '1.0.0'
                }
            }
        }
    }
}