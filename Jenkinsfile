pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Docker Build') {
         steps {
            sh(script: 'docker compose build')
            // powershell(script: 'docker images -a')
            // powershell(script: """
            //      cd azure-vote/
            //      docker images -a
            //      docker build -t jenkins-pipeline .
            //      docker images -a
            //      cd ..
            //      """ )
         }
      }
      stage('Start App') {
         steps {
            sh(script: 'docker compose up -d')
         }
      }
      stage('Run Tests') {
         steps {
            echo "Running tests)"
         }
         post {
            success {
               echo "Tests passed! :)"
            }
            failure {
               echo "Tests failed :("
            }
         }
      }
<<<<<<< HEAD
      stage('Docker Push') {
         steps {
            echo "Running in $WORKSPACE"
            dir("$WORKSPACE/azure-vote")
            sh(script:{
                  docker.withRegistry('',dockerhub){
                     def image = docker.build('stevesam/jenkins-course')
                     image.push()
                  }
            })
         }
      }
=======
>>>>>>> d8dbc6dd2ca2862ddf65b0839ffc204f928e9914
   }
   post {
      always {
         sh(script: 'docker compose down')
      }
   }
}
