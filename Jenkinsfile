pipeline {
    agent {
        node 'slave01'
    }
    options {
        timestamps()
    }
    stages {
        stage('Pull image 1') {
            steps {
                def image = docker.image("python:3.6.12-alpine")
                image.pull()

            }
        }
        stage('Pull image 2') {
            steps {
                scripts {
                    try {
                        def image = docker.image("pajfon:3.6.12-elpajn")
                        image.pull()
                    } catch (err) {
                        currentBuild.result = 'UNSTABLE'
                    }
                }

            }
        }
    }
}