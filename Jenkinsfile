pipeline{
    agent {
        label 'agent1'
    }
    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('build'){
            steps{
                sh "mvn clean install"
            }
        }
        stage ('test'){
            steps{
                sh "mvn test"
            }
        }
    }
}
//hi

