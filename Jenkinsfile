node {
  def app

  stage('Clone repository') {
    checkout scmGit(branches: [
      [name: '*/gcp']
    ], extensions: [], userRemoteConfigs: [
      [credentialsId: 'github', url: 'https://github.com/vinay-mirvin/kubernetescode.git']
    ])
  }

  stage('Build image') {

    script {
      withDockerRegistry(credentialsId: 'gcr:ornate-unity-358911', url: 'https://asia-south1-docker.pkg.dev') {
        app = docker.build("asia-south1-docker.pkg.dev/ornate-unity-358911/test-0/flask-app:$BUILD_NUMBER")
        app.push()
      }
    }
  }

}