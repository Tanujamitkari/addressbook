pipeline {
    agent none

    tools{
        jdk 'myjava'
        maven 'mymavan'
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
                            sh "scp -o StrictHostKeyChecking=no server-script.sh ec2-user@172.31.33.81:/home/ec2-user"
                            sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.33.81 ~ec2-user/server-script.sh"
                            //sh "ssh ec2-user@172.31.33.81 sudo docker build -t imagename /home/ec2-user/addressbook"

                        }
                    }
                }
                
            }

}
