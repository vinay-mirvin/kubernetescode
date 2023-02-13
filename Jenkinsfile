node {
  def app

//   stage('Clone repository') {
//     checkout scmGit(branches: [
//       [name: '*/gcp']
//     ], extensions: [], userRemoteConfigs: [
//       [credentialsId: 'github', url: 'https://github.com/vinay-mirvin/kubernetescode.git']
//     ])
//   }



    stage('Clone repository') {
      

        checkout scm
    }


  stage('Build image') {

    script {
      withDockerRegistry(credentialsId:'gcr:ornate-unity-358911', url: 'https://asia-south1-docker.pkg.dev') {
        app = docker.build("asia-south1-docker.pkg.dev/ornate-unity-358911/test-0/flask1:$BUILD_NUMBER")
        app.push()
      }
    }
  }


//     stage('Deploy') {
//     echo "triggering Deploy_app"
//     // echo params.DEPLOY 
//     if ( params.DEPLOY == 'BUILD_AND_DEPLOY'){
//         build job: 'Deploy_app', parameters: [
//             string(name: 'IMAGE_TAG', value: env.BUILD_NUMBER),
//             string(name: 'REPOSITORY', value: 'asia-south1-docker.pkg.dev/ornate-unity-358911/test-0/flask-app'),
//             string(name: 'ENVIRONMENT_NAME', value: env.ENVIRONMENT_NAME),
//             string(name: 'APPLICATION_NAME', value: env.APPLICATION_NAME),
//             string(name: 'APPLICATION_INTERNAL_PORT_NUMBER', value: env.APPLICATION_INTERNAL_PORT_NUMBER)             
//         ]
//     }
//    }


}


