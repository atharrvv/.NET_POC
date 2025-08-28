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
        
        // stage ('Image scanning') {
        //     steps {
        //         script {
        //             sh '''
        //                 trivy image eatherv/database:latest \
        //                     --severity LOW,MEDIUM,HIGH \
        //                     --exit-code 0 \
        //                     --quiet \
        //                     --format json -o database_trivy_medium.json

                        
        //                 trivy image eatherv/database:latest \
        //                     --severity CRITICAL \
        //                     --quiet \
        //                     --exit-code 0 \
        //                     --format json -o database_trivy_critical.json 

        //             '''
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
        
        // stage ('Backend Build') {
        //     steps {
        //         script {
        //             docker.build('eatherv/backend:latest', './TextEditor/')
        //         }
        //     }
        // }

        // stage ('Backend Image Scanning') {
        //     steps {
        //         script {
        //             sh '''
        //                 trivy image eatherv/backend:latest \
        //                     --severity LOW,MEDIUM,HIGH \
        //                     --quiet \
        //                     --exit-code 0 \
        //                     --format json -o backend_trivy_medium.json

        //                 trivy image eatherv/backend:latest \
        //                     --severity CRITICAL \
        //                     --quiet \
        //                     --exit-code 0 \
        //                     --format json -o backend_trivy_high.json
                            
        //             '''
        //         }
        //     }
        // }
        
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
        stage ('K8s namespaces scanning') {
            steps {
                script {
                    sh '''
                        trivy k8s --severity LOW,MEDIUM,HIGH --format json -o namespace_high.json --namespace app --report summary all
                        
                        trivy k8s --severity CRITICAL --format json -o namespace_critical.json --namespace app --reprot summary all
                    '''
                }
            }
        }
        stage ('K8s pod scanning') {
            steps {
                script {
                    sh '''
                        trivy k8s --severity LOW,MEDIUM,HIGH --fromat json -o pod_high.json --namespace app pod  python-application-dc45697c9-c9n9l

                        trivy k8s --severity CRITICAL --format json -o pod_critical --namespace app pod python-application-dc45697c9-c9n9l                     
                    '''
                }
            }
        }
    }
}
