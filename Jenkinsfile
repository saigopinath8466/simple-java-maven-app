pipeline{
    agent {
        label 'agent1'
    }
    tools {
        maven 'maven362'
    }

    options {
        timeout(10)
       buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')
    }

    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('build'){
            steps{
                sh "mvn clean install -DskipTests"
            }
        }
        stage ('test'){
            steps{
                sh "mvn test"
                junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'
            }
        }
        stage ('deploy'){
            steps{
                echo "deploying Dev environment"
                sshagent(['maven-cd-jenkins']) {
                    sh "scp -o StrictHostKeyChecking=no target/my-app-1.0-SNAPSHOT.jar ec2-user@172.31.61.116:/home/ec2-user"
                }
            }
        }
    }
    post {
        always {
           deleteDir()
         }
        failure {
            echo "sendmail -s Maven Job Failed recipients@mycompany.com"
         }
        success {
             echo "the job is successful"
         }
        
    }
}



