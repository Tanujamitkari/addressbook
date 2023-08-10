pipeline {
    agent none

    tools{
        //jdk 'myjava'
        maven 'mymavan'
    }
    environment{
        IMAGE_NAME='devopstrainer/java-mvn-privaterepos:$BUILD_NUMBER'
        BUILD_SERVER_IP='ec2-user@172.31.33.81'
    }


    stages {
                stage('compile') {
                    agent any
                    steps {
                        echo "compile the code"
                        sh 'mvn compile'
                    }
                }
                stage('unit test') {
                    agent any
                    steps {
                        echo 'run the test cases'
                        sh 'mvn test'
                    }
                    post{
                        always{
                            junit 'target/surefire-reports/*.xml'
                        }
                    }
                }
                stage('package') {
                    //agent {label 'linux_slave'}
                    agent any
                    //on slave2
                    steps {
                        sshagent(['build-server-key']) {
                        
                            echo "package the code"
                            //sh 'mvn package'
                            sh "scp -o StrictHostKeyChecking=no server-script.sh ${BUILD_SERVER_IP}:/home/ec2-user"
                            sh "ssh -o StrictHostKeyChecking=no ${BUILD_SERVER_IP} bash ~ec2-user/server-script.sh"
                            sh "ssh ${BUILD_SERVER_IP} sudo docker build -t ${IMAGE_NAME} /home/ec2-user/addressbook"
                            sh "ssh ${BUILD_SERVER_IP} sudo docker login -u tanuja02 -p pwd"


                        }
                    }
                }
                
            }

}
