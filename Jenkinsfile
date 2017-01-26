pipeline {
    agent { 
        label 'mini' 
    }

    triggers {
        cron '@daily'
    }

    stages {
        stage('git') {
            checkout scm
        }

        stage('build') {
            sh 'docker build .'
        }

        // stage('tests') {
        //     sh 'validate somehow...?'
        // }

        // stage('push') {
        //     sh 'docker push ...'
        // }
    }
}
