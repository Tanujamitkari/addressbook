pipeline {
    agent any

    parameters{
        string(name:'Env',defaultValue:'Test',description:'Env to deploy')
        booleanParam(name:'executeTests',defaultValue:true,description:'decide to run tc')
    }

    stages {
        stage('compile') {
            steps {
                echo 'compile the code'
            }
        }
        stage('unit test') {
            when{
                expression{
                    params.executeTests == true
                }
            }
            steps {
                echo 'run the test cases'
            }
        }
        stage('package') {
            steps {
                echo "package the code in env:${params.Env}"
            }
        }
    }
}
