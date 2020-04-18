pipeline {

    agent any

     
    stages {
        
        stage ('checkout'){
            steps {
            git  'https://github.com/SAKTHISIVANI18/jenkinfile.git'
            }
        }
       stage ('package') {

            steps {


                    sh './mvnw clean package'

            }

         }
      
         stage('Quality Analysis') {
            
                     
                    steps {
                        echo 'Run integration tests here...'
                    }
                }
                stage('Sonar Scan') {
                    agent {
                        docker {
                           
                            reuseNode true
                            image 'maven:3.6.3-jdk-13.0.1'
                        }
                    }
                    environment {
                       
                        SONAR = credentials('sonar')
                    }
                    steps {
                        sh 'mvn sonar:sonar -Dsonar.login=$SONAR_PSW'
                    }
                }
            }
        }
    
