pipeline {
    
    parameters {
        booleanParam(name: 'MERGE_MASTER', defaultValue: false, description: '')
        string(name: 'DEPLOY_ENV', defaultValue: 'staging', description: '')
    }
    
    agent any

    stages {

        stage('Configure'){
            steps {
                step([$class: 'WsCleanup'])
                checkout scm
            }
        }

        stage('Example') {
            steps {
                echo 'Hello World'
                sh '''
                echo $DEPLOY_ENV
                env | sort
                git status
                if [ "$MERGE_MASTER" = 'true' ]]; then 
                    git merge origin/master
                fi
                
                '''
            }
        }
    }
}