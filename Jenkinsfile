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
    stage ('Application save') {
      steps {
        script {
          sh "docker save -o application.tar application"
        }
      }
    }
    stage ('Migration to another server') {
      steps {
        scripts {
          sh "scp application.tar clone:~/"
        }
      }
    }
    stage ('Loading the image from .tar') {
      steps {
        scripts {
          sh """ ssh clone "docker load -i ~/application.tar" """
        }
      }
    }
  }  
}
