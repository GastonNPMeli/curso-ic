pipeline {
    agent any
    triggers {
        pollSCM('H/2 * * * *')
    }
    stages {
        stage('Build') {
         steps {
             sh "./gradlew build"
         }
         post{
            always{

                println "ava se exportan los resultados de los test unitarios"
            }
         }

        }
        stage('Deploy') {
          steps {
              sh "./gradlew deploy"
          }
        }
        stage('Verify') {
           steps {
               sh "./gradlew verify"
           }
           post{
               always{

                   println "ava se exportan los resultados de los test de aceptación"
               }
           }
        }

    }
    post {
        success {
            echo 'El job finalizó OK! :)'
        }
        failure {
            echo 'El job rompio! :('
        }
    }
}