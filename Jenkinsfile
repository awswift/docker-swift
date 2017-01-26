pipeline {
    agent { 
        label 'mini' 
    }

    triggers {
        cron '@daily'
    }

    stages {
        stage('git') {
            steps {
                checkout scm
            }
        }

        stage('build') {
            steps {
                sh 'docker build .'
            }
        }

        // stage('tests') {
        //     sh 'validate somehow...?'
        // }

        // stage('push') {
        //     sh 'docker push ...'
        // }
    }
}
