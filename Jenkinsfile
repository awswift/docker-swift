properties([
    pipelineTriggers([
        cron('@daily'),
        [$class: 'GitHubPushTrigger']
    ])
])

node('mini') {
    stage('git') {
        checkout scm
    }

    stage('build') {
        sh 'docker build .'
    }

    // stage('tests') {
    //     sh 'validate somehow...?'
    // }

    // if (env.BRANCH_NAME == 'master') {
    //     stage('push') {
    //         sh 'docker push ...'
    //     }
    // }
}
