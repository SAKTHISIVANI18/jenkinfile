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
      stage ('sonar') {

          steps {


                sh 'sonar-scanner'

           }
      }
         stage('Quality Analysis') {
            parallel {
                
                stage('Integration Test') {
                    agent any  
                    steps {
                        echo 'Run integration tests here...'
                    }
                }
                stage('Sonar Scan') {
                    agent {
                        docker {
                           
                            reuseNode true
                            image 'maven:3.5.0-jdk-8'
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
    }
