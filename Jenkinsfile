pipeline {

    agent any

     
    stages {
        
        stage ('checkout'){
            steps {
            git  'https://github.com/SAKTHISIVANI18/jenkinfile.git'
            }
        }
        stage('build'){
            steps{
            
            
         withSonarQubeEnv('SonarCloud') {
    sh "./mvnw org.jacoco:jacoco-maven-plugin:prepare-agent verify \
        sonar:sonar -Dsonar.branch.name=${env.BRANCH_NAME}"
}
            }
        }

        
        stage ('static code analysis'){
            steps{


def urlcomponents = env.CHANGE_URL.split("/")
def org = urlcomponents[3]
def repo = urlcomponents[4]
withSonarQubeEnv('SonarCloud') {
    sh "./mvnw sonar:sonar \
    -Dsonar.pullrequest.provider=GitHub \
    -Dsonar.pullrequest.github.repository=${org}/${repo} \
    -Dsonar.pullrequest.key=${env.CHANGE_ID} \
    -Dsonar.pullrequest.branch=${env.CHANGE_BRANCH}"
}
            }
            }
        }
        }
