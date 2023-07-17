pipeline {
    agent any

    parameters{
        string(name:'Env',defaultvalue:'Test',description:'Env to deploy')
    }

    stages {
        stage('compile') {
            steps {
                echo 'compile the code'
            }
        }
        stage('unit test') {
            steps {
                echo 'run the test cases'
            }
        }
        stage('package') {
            steps {
                echo 'package the code'
            }
        }
    }
}
