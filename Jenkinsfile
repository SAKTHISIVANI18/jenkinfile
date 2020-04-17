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


                    sh './mvn clean package'

            }

         }

        
        stage ('deploy') {
            
           
            steps {

              sh 'cp target/*war /home/dineshreddy99077/noida/apache-tomcat-7.0.103/webapps/'

            }
            }
     
        

    }
}
