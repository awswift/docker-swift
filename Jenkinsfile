properties([
    pipelineTriggers([
        cron('@daily'),
        [$class: 'GitHubPushTrigger']
    ])
])

def doit() {
    stage('git') {
        checkout scm
    }

    stage('build') {
        sh 'docker build --no-cache .'
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

node('mini') {
    ansiColor('xterm') {
        timestamps {
            timeout(30) {
                doit()
            }
        }
    }
}

