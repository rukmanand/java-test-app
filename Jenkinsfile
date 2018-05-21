node {
  stage('SCM Checkout') {
    git 'https://github.com/rukmanand/java-test-app'
  }
  stage('Compile package') {
    sh 'mvn package'
  }
}
