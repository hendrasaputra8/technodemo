node {
      env.NODEJS_HOME = "${tool 'node12' }"
      env.PATH="${env.NODEJS_HOME}/bin:${env.PATH}"

      stage('Prepare') {
          checkout scm
      }

      stage('Build') {
          sh 'npm install'
      }

 //     stage('Test') {
 //         sh 'npm test'
 //     }

 //     stage('Test e2e') { 
 //         sh 'npm run test:e2e'
 //     }

      stage('Deploy') {
        withCredentials([string(credentialsId: 'heroku-token', variable: 'TOKEN')]) {
            sh 'git push https://:${TOKEN}@git.heroku.com/techno-app.git HEAD:main'
        }
      }
}