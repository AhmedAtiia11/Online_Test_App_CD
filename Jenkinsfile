node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                  // Don't Forget to give username and tokken to Jenkins
                  
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                      // give the configuration to git
                        sh "git config user.email ahmedatya1288@gmail.com"
                        sh "git config user.name AhmedAtiia11"
                      
                      // Modify Django Deployment file with the new version "taken from the CI pipeline" 
                        sh "echo 'Modifying Django Deployment'"                     
                        sh "cat app/Django-deployment.yaml"
                        sh "sh django_app_version_update app/Django-deployment.yaml"
                        sh "echo $GIT_COMMIT_REV"
                        sh "cat app/Django-deployment.yaml"

                      // Modify React Deployment file with the new version "taken from the CI pipeline" 
                        sh "echo 'Modifying React Deployment'"                     
                        sh "cat app/React-deployment.yaml"
                        sh "sh react_app_version_update app/React-deployment.yaml"
                        sh "echo $GIT_COMMIT_REV"
                        sh "cat app/React-deployment.yaml"

                      // MOdify the CD Repo with the new app  
                        sh "git add *"
                        sh "git commit -m 'Done by Jenkins Job changemanifest file: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/Online_Test_App_CD/ HEAD:main"
                        // sh 'echo $GIT_USERNAME'
      }
    }
  }
}
}
