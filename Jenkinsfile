pipeline {
    agent any
    
    stages {
        stage('Git Clone') {
            steps {
                git branch: 'trial', credentialsId: 'git', url: 'https://github.com/atharrvv/.NET_POC.git'
            }
        }
        stage('Database Build') {
            steps {
                script {
                    docker.build('eatherv/database:latest', './TextEditor/database')
                }
            }
        }
        stage ('DockerHub'){
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker'){
                        docker.image("eatherv/database:latest").push()
                    }
                }
            }
        }
        stage ('Database Container') {
            steps {
                script {
                    sh "docker run --name database -d -p 1433:1433 eatherv/database:latest"
                }
            }
        }
        stage ('Inject IP into appsettings.json'){
            steps {
                script {
                    // Get public IP
                    def instanceIp = sh(script: "curl -s ifconfig.me", returnStdout: true).trim()
                    // Update appsettings.json
                    sh """
                        jq '.ConnectionStrings.DefaultConnection |= sub("Server=[^,]+"; "Server=${instanceIp}")' appsettings.json > appsettings.tmp.json && mv appsettings.tmp.json appsettings.json
                    """
                }
            }
        }
        stage ('Backend Build') {
            steps {
                script {
                    docker.image('eatherv/backend:latest', '.TextEditor/')
                }
            }
        }
        stage ('Backend DockerHub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker'){
                        docker.image("eatherv/backend:latest").push()
                    }
                 }
              }
            }
        
    }
}
