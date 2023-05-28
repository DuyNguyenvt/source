node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'node -v'
    //   sh 'docker -v'
    //   sh 'printenv'
    }
    // stage('Build Docker test'){
    //  sh 'docker build -t react-test -f Dockerfile.test --no-cache .'
    // }
    // stage('Docker test'){
    //   sh 'docker run --rm react-test'
    // }
    // stage('Clean Docker test'){
    //   sh 'docker rmi react-test'
    // }
    stage('Deploy'){
    //   if(env.BRANCH_NAME == 'master'){
        // sh 'docker build -t react-app --no-cache .'
        // sh 'docker tag react-app localhost:5000/react-app'
        // sh 'docker push localhost:5000/react-app'
        // sh 'docker rmi -f react-app localhost:5000/react-app'
        sh 'pwd'
        // sh 'node -v'
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