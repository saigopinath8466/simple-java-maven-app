pipeline{
    agent {
        label 'dockernode'
    }
    tools {
        maven 'maven362'
    }
    environment {
        target_user = "ec2-user"
        target_server = "172.31.61.116"
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
       // stage ('deploy to dev') {
            //parallel {
              //  stage('target1') {
                 //   environment {
                   //     target_user = "ec2-user"
                   //     target_server = "172.31.61.116"
                  //  }
                
                   // steps{
//                     echo "deploying Dev environment"
                      //  sshagent(['maven-cd-jenkins']) {
                    //        sh "scp -o StrictHostKeyChecking=no target/my-app-1.0-SNAPSHOT.jar $target_user@$target_server:/home/ec2-user"
                   //     }
                    }
             //   }
            //   stage('target2') {
              //      environment {
                   //     target_user = "ec2-user"
                 //       target_server = "172.31.24.134"
                //     }
                
               //     steps{
                   //     echo "deploying Dev environment"
//                       sshagent(['maven-cd-jenkins']) {
                   //         sh "scp -o StrictHostKeyChecking=no target/my-app-1.0-SNAPSHOT.jar $target_user@$target_server:/home/ec2-user"
                 //       }
             //       }
             //   }
            //    stage ('Deploy to UAT') {
             //       input {
              //         message 'Do you want me to Deploy to UAT?'
             //       }
                //    environment {
               //         target_user = "ec2-user"
                 //       target_server = ""
                  //  }
                   // steps {
               //         echo "awaiting"
                //    }
                }//
                
           // }
           
       // }
   // }
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


/*stage ('deploy'){
            steps{
                echo "deploying Dev environment"
                sshagent(['maven-cd-jenkins']) {
                    sh "scp -o StrictHostKeyChecking=no target/my-app-1.0-SNAPSHOT.jar $target_user@$target_server:/home/ec2-user"
                }
            }
        }
*/

