pipeline {
    agent any

    parameters{
        string(name:'Env',defaultValue:'Test',description:'Env to deploy')
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
                echo "package the code in env:${params.env}"
            }
        }
    }
}
