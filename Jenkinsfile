pipeline {
    agent any

    parameters{
        string(name:'Env',defaultValue:'Test',description:'Env to deploy')
        booleanParam(name:'executeTests',defaultValue:true,description:'decide to run tc')
        choice(name:'APPVERSION',choices:['1.1','1.2','1.3'])
    }

    stages {
        stage('compile') {
            steps {
                echo "compile the code ${params.APPVERSION}"
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
        stage('Deploy') {
            input{
                message "provide approval for prod"
                ok "Deploy to prod"
                parameters{
                    booleanParam(name:'DEPLOYTOPROD',defaultValue:false,description:'decide to deploy on prod')
                }
            }
            steps {
                echo "package the code in env:${params.Env}"
    }
        }
}
