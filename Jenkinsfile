pipeline{
    agent {
        label 'agent1'
    }
    tools {
        maven 'maven362'
    }

    options {
        timestamps
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
        stage ('post task'){
            steps{
                sh "echo send an email"
            }
        }
    }
}



