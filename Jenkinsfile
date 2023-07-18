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
                    agent {label 'linux_slave'}
                    steps {
                        echo "package the code"
                        sh 'mvn package'
                    }
                }
                
            }

}
