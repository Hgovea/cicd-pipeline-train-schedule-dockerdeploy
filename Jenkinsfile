pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        steps {
            script {
                app = docker.build("<DOCKER_HUB_USERNAME>/train-schedule")
                app.inside {
                    sh 'echo $(curl localhost:8080)'
                }
             }
         }
       }
