node {
  stage('SCM Checkout') {
    git 'https://github.com/rukmanand/java-test-app'
  }
  stage('Compile package') {
    sh 'mvn package'
  }
  stage('S3 upload') {
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'jenkins-s3']]) {
       //s3Upload(file:'mytest-0.0.1.war', bucket:'jenkins-uploads-rkm', path:'/var/lib/jenkins/workspace/jenkins-practice/target/mytest-0.0.1.war')
      s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'jenkins-uploads-rkm', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: true, selectedRegion: 'ap-south-1', showDirectlyInBrowser: false, sourceFile: '*', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'jenkinsuploadingtos3', userMetadata: []
    }
  }
}
