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
        sh """
            docker build \
            --no-cache \
            --build-arg SWIFT_BRANCH=development \
            --build-arg SWIFT_VERSION=swift-DEVELOPMENT-SNAPSHOT-2017-01-24-a \
            .
        """
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

