node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'node -v'
    }

    stage('Extract Envs') {
      if (fileExists('.env.prod')) {
        echo ".env.prod exists"
        envInject {
          // Provide the path to the environment file in the Git repository
          propertiesFile('env.prod')
        }
         echo "test env: ${env.PROJECT_ID}"
      } else {
        echo ".env.prod does not exist"
      }
    }
    stage('Build Docker test'){
    }
    stage('Deploy'){
        sh 'pwd'
        sh 'npm install'
        sh 'npm run build'
        sh 'pwd'
        try {
          sh 'rm -rf ../../fe-build/*'
        } catch (Exception e) {
          echo "Folder does not exist on the first run! It should be good!"
        }   
        sh 'cp -r ./build/* ../../fe-build'
    }
  }
  catch (err) {
    throw err
  }
}