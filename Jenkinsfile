node {
  stage('SCM Checkout') {
    git 'https://github.com/rukmanand/java-test-app'
  }
  stage('Compile package') {
    sh 'mvn package'
  }
  stage('S3 upload') {
    withAWS(profile:'jenkinsUploadToS3') {
      s3Upload(file:'mytest-0.0.1.war', bucket:'jenkins-uploads-rkm', path:'/var/lib/jenkins/workspace/jenkins-practice/target/mytest-0.0.1.war')
    }
  }
}
