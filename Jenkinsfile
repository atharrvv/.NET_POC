pipeline {
    agent any
    
    stages {
        // stage('Database Build') {
        //     steps {
        //         script {
        //             docker.build('eatherv/database:latest', './TextEditor/database')
        //         }
        //     }
        // }
        // stage ('Database DockerHub'){
        //     steps {
        //         script {
        //             docker.withRegistry('https://index.docker.io/v1/', 'docker'){
        //                 docker.image("eatherv/database:latest").push()
        //             }
        //         }
        //     }
        // }
        // stage ('Database Container') {
        //     steps {
        //         script {
        //             sh "docker run --name database -d -p 1433:1433 eatherv/database:latest"
        //         }
        //     }
        // }
        stage ('Backend Build') {
            steps {
                script {
                    sh "docker build -t backend ."
                    // docker.build('eatherv/backend:latest', './TextEditor/')
                }
            }
        }
        // stage ('Backend DockerHub') {
        //     steps {
        //         script {
        //             docker.withRegistry('https://index.docker.io/v1/', 'docker'){
        //                 docker.image("eatherv/backend:latest").push()
        //             }
        //          }
        //       }
        //     }
        // stage ('Backend Container') {
        //     steps {
        //         script {
        //             sh "docker run --name backend -d -p 8080:80 eatherv/backend:latest"
        //         }
        //     }
        // }
    }
}
