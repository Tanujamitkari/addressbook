pipeline {
    agent any

    tools{
        jdk 'myjava'
        maven 'mymaven'
    }


    stages {
                stage('compile') {
                    steps {
                        echo "compile the code"
                        sh 'mvn compile'
                    }
                }
                stage('unit test') {
                    
                    steps {
                        echo 'run the test cases'
                        sh 'mvn test'
                    }
                }
                stage('package') {
                    steps {
                        echo "package the code"
                        sh 'mvn package'
                    }
                }
                
            }

}
