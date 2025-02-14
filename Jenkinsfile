pipeline {
  agent any
  stages {
    // stage ('Databasae Build') {
    //   steps {
    //     script {
    //       docker.build('database', './TextEditor/database')
    //     }
    //   }
    // }
    // stage ('Database Container') {
    //   steps {
    //     script {
    //       sh "docker run --name database -d -p 1433:1433 database"
    //     }
    //   }
    // }
    // stage ('Database Save') {
    //   steps {
    //     script {
    //       sh ""
    //     }
    //   }
    // }
    // stage ('Database copy to another server') {
    //   steps {
    //     script {
    //       sh
    //     }
    //   }
    // }
    // stage ('Database load image') {
    //   steps {
    //     script {
    //       sh ""
    //     }
    //   }
    // }
    // stage ('Database container run') {
    //   steps {
    //     script {
    //       sh ""
    //     }
    //   }
    // }
    // stage ('Application Build') {
    //   steps {
    //     script {
    //       docker.build('application', './TextEditor/')
    //     }
    //   }
    // }
    // stage ('Appliocation container run') {
    //   steps {
    //     script {
    //       sh "docker run --name application -d -p 8080:80 application"
    //     }
    //   }
    // }
    stage ('Application save') {
      steps {
        script {
          sh "docker save -o  application.tar application"
        }
      }
    }
    stage ('Migration to another server') {
      steps {
        script {
          sh "scp application.tar clone@20.127.210.47:~/"
        }
      }
    }
    stage ('Loading the image from .tar') {
      steps {
        script {
          sh """ ssh clone "docker load -i ~/application.tar" """
        }
      }
    }
  }  
}
