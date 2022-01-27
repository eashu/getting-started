pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent {
        label 'ubuntu-1804 && amd64 && docker'
    }
    stages {
        stage('build and push') {
            when {
                branch 'master'
            }
            sh "docker build -t docker/getting-started ."

            steps {
                withDockerRegistry(credentialsId: 'Docker', url: 'https://hub.docker.com/') {
                    sh("docker push docker/getting-started")
                }
            }
        }
    }
}
